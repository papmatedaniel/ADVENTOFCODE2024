using System;
using System.IO;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Diagnostics.CodeAnalysis;


class Program
{
	static void Main(string[] args)
	{

		string[] beolvas = File.ReadAllLines("input.txt", Encoding.UTF8);
		int hanybiztonsagos = 0;
		List<List<int>> szamok2 = new List<List<int>>();
		foreach (var item in beolvas)
		{
			List<int> sorszamok = new List<int>();
			foreach (var szam in item.Split())
			{
				sorszamok.Add(Convert.ToInt32(szam));
			}
			szamok2.Add(sorszamok);
		}
		foreach (var szamok in szamok2)
		{
			bool igaze = true;
			int novvagycsokk = 1;
			if (szamok[0] > szamok[1])
			{
				novvagycsokk = -1;
			}

			for (int i = 0; i < szamok.Count - 1; i++)
			{
				if (szamok[i] < szamok[i + 1] && novvagycsokk == -1 || szamok[i] > szamok[i + 1] && novvagycsokk == 1 || (Math.Abs(szamok[i] - szamok[i + 1]) < 1 || Math.Abs(szamok[i] - szamok[i + 1]) > 3))
				{
					igaze = false;
					break;
				}
			}
			if (igaze)
			{
				hanybiztonsagos++;
			}
		}





		Console.WriteLine(hanybiztonsagos);
		Console.WriteLine("Nyomj entert");
		Console.ReadKey();
	}

}
