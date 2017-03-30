# es16
#include <stdio.h>

/* Es.1 */
int zaino(int pesi[], int n, int p) 
{
	if (p > 0)
	{
		if (n == 1)
		{
			if (pesi[0] == p) 
				return 1;
			else 
				return 0;
		}
		else 				
			return (zaino(pesi, n-1, p-pesi[n-1]) || zaino(pesi, n-1, p));
	}
	else
	{
		if (p == 0)
			return 1;
		else 
			return 0;				
	}	
}


/* Es.2 */
int funz_min (int v[ ], int n)
{
	if (n == 1)
		return v[n-1];
	else
	{
		if (n == 2)
		{
			if (v[n-2] < v[n-1]) 
				return v[0];
			else 
				return v[1];
		}
		else 
		{
			int min = funz_min(v, n-1);
			if (v[n-1] < min) 
				return v[n-1];
			else 
				return min; 
		}
	}
}

int conta_combinazioni(int v[], int n, int somma) 
{
	int ris = 0;
	if (n > 0)
	{
		if (somma > 0)
		{
			if (somma == funz_min (v, n))	
				return 1;
			else 
			{
				ris += conta_combinazioni (v, n, somma-v[0]) + conta_combinazioni (v+1, n-1, somma);
				return ris;
			}
		}
		else
		{
			if (somma == 0)
				return 1;
			else 
				return 0;
		}
	}
	else 
		return 0;
}
