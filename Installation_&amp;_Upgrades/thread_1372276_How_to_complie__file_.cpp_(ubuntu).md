---
title: "How to complie  file .cpp (ubuntu)"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by sugussugus on 2010-01-04
I have TestTime.cpp




/* test-time.cpp */
// Testing time management


#include <iostream>
#include <cmath>
#include "./gpstk/DayTime.hpp"


using namespace std;
using namespace gpstk;


int main()
{

   cout << fixed << setprecision(3);   // Set a proper output format

   DayTime epoch1(2009,10,28,10,30,0.0);

   DayTime epoch2 = epoch1 + 3600.0;

   cout << epoch1 << endl
        << epoch2 << endl;

   cout << epoch1.GPSfullweek() << " "
        << epoch1.DOY()         << " "
        << epoch1.GPSsecond()   << endl;

   return 0;

}




I used  **gcc -o test TestTime.cpp** to creat a make file, but I have an problem: error



/tmp/ccI11Fmz.o: In function `std::__verify_grouping(char const*, unsigned int, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
TestTime.cpp.text+0xe): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::size() const'
TestTime.cpp.text+0x59): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >erator[](unsigned int) const'
TestTime.cpp.text+0x97): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >erator[](unsigned int) const'
TestTime.cpp.text+0xdf): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >erator[](unsigned int) const'
/tmp/ccI11Fmz.o: In function `__static_initialization_and_destruction_0(int, int)':
TestTime.cpp.text+0x129): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccI11Fmz.o: In function `__tcf_0':
TestTime.cpp.text+0x176): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccI11Fmz.o: In function `main':
TestTime.cpp.text+0x1af): undefined reference to `std::cout'
TestTime.cpp.text+0x1b4): undefined reference to `std::basic_ostream<char, std::char_traits<char> >erator<<(std::ios_base& (*)(std::ios_base&))'
TestTime.cpp.text+0x1c5): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& stderator<< <char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, std::_Setprecision)'
TestTime.cpp.text+0x206): undefined reference to `gpstk:ayTime:ayTime(short, short, short, short, short, double, gpstk:ayTime::TimeFrame)'
TestTime.cpp.text+0x222): undefined reference to `gpstk:ayTimeerator+(double) const'
TestTime.cpp.text+0x233): undefined reference to `std::cout'
TestTime.cpp.text+0x23: undefined reference to `gpstkerator<<(std::basic_ostream<char, std::char_traits<char> >&, gpstk:ayTime const&)'
TestTime.cpp.text+0x240): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
TestTime.cpp.text+0x24: undefined reference to `std::basic_ostream<char, std::char_traits<char> >erator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
TestTime.cpp.text+0x259): undefined reference to `gpstkerator<<(std::basic_ostream<char, std::char_traits<char> >&, gpstk:ayTime const&)'
TestTime.cpp.text+0x261): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
TestTime.cpp.text+0x269): undefined reference to `std::basic_ostream<char, std::char_traits<char> >erator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
TestTime.cpp.text+0x282): undefined reference to `gpstk:ayTime:OY() const'
TestTime.cpp.text+0x291): undefined reference to `gpstk:ayTime::GPSfullweek() const'
TestTime.cpp.text+0x29d): undefined reference to `std::cout'
TestTime.cpp.text+0x2a2): undefined reference to `std::basic_ostream<char, std::char_traits<char> >erator<<(short)'
TestTime.cpp.text+0x2b2): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& stderator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
TestTime.cpp.text+0x2c1): undefined reference to `std::basic_ostream<char, std::char_traits<char> >erator<<(short)'
TestTime.cpp.text+0x2d1): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& stderator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
TestTime.cpp.text+0x2e0): undefined reference to `std::basic_ostream<char, std::char_traits<char> >erator<<(double)'
TestTime.cpp.text+0x2e: undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
TestTime.cpp.text+0x2f0): undefined reference to `std::basic_ostream<char, std::char_traits<char> >erator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccI11Fmz.o: In function `gpstk:ayTime::GPSsecond() const':
TestTime.cpp.text._ZNK5gpstk7DayTime9GPSsecondEv[gpstk:ayTime::GPSsecond() const]+0xd): undefined reference to `gpstk:ayTime::GPSsow() const'
/tmp/ccI11Fmz.o.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status



I don't why?

Could you help me?

---

### Post by pben_harris on 2010-01-20
Sorry if this is a repost, I didn't see my prior reply show up.

Basically you have to tell the compiler (which in this case doubles as the linker) where to find the include files and where to find the libraries you need. And where those are depend on how you've installed the GPSTk. The -I (note that is a capital i) option tells the compiler where to find .hpp files. The -L and -l (lower case L) are used in conjunction to specify which libraries to use.

Regards,
Ben Harris

---

