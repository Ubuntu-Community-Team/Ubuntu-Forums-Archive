---
title: "dvorakng: need help to install"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by fantasmino on 2008-07-23
Hi,
I really need help to install this typing tutor. I search in google and in the forums, but nothing...
You can find dvorakng here:
[http://freshmeat.net/projects/dvorakng/](http://freshmeat.net/projects/dvorakng/)
the readme is very simple, I follow the suggestions but I can't install it. Someone can help me?
Here the error output:
```
$ make
g++ -g0 -O2 -fmessage-length=0 -Wall    -c -o dvorakng.o dvorakng.cpp
dvorakng.cpp:46:20: error: curses.h: Nessun file o directory
dvorakng.cpp:70: error: expected constructor, destructor, or type conversion before ‘*’ token
dvorakng.cpp: In function ‘char* OnOffFrom01(bool)’:
dvorakng.cpp:258: warning: deprecated conversion from string constant to ‘char*’
dvorakng.cpp:262: warning: deprecated conversion from string constant to ‘char*’
dvorakng.cpp:266: warning: deprecated conversion from string constant to ‘char*’
dvorakng.cpp: In function ‘void ConfigMenu()’:
dvorakng.cpp:393: error: ‘noecho’ was not declared in this scope
dvorakng.cpp:394: error: ‘FALSE’ was not declared in this scope
dvorakng.cpp:394: error: ‘curs_set’ was not declared in this scope
dvorakng.cpp:396: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:396: error: ‘attron’ was not declared in this scope
dvorakng.cpp:402: error: ‘clear’ was not declared in this scope
dvorakng.cpp:403: error: ‘COLOR_PAIR’ was not declared in this scope
dvorakng.cpp:405: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp:434: error: ‘getch’ was not declared in this scope
dvorakng.cpp:470: error: ‘attroff’ was not declared in this scope
dvorakng.cpp:568: error: ‘echo’ was not declared in this scope
dvorakng.cpp:569: error: ‘TRUE’ was not declared in this scope
dvorakng.cpp:570: error: ‘attroff’ was not declared in this scope
dvorakng.cpp: In function ‘void Error(const std::string&)’:
dvorakng.cpp:692: error: ‘clear’ was not declared in this scope
dvorakng.cpp:693: error: ‘noecho’ was not declared in this scope
dvorakng.cpp:694: error: ‘FALSE’ was not declared in this scope
dvorakng.cpp:694: error: ‘curs_set’ was not declared in this scope
dvorakng.cpp:695: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:695: error: ‘attron’ was not declared in this scope
dvorakng.cpp:696: error: ‘COLOR_PAIR’ was not declared in this scope
dvorakng.cpp:697: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp:702: error: ‘getch’ was not declared in this scope
dvorakng.cpp:704: error: ‘TRUE’ was not declared in this scope
dvorakng.cpp:705: error: ‘echo’ was not declared in this scope
dvorakng.cpp: In function ‘int myGetch(char)’:
dvorakng.cpp:712: error: ‘getch’ was not declared in this scope
dvorakng.cpp:714: error: ‘ERR’ was not declared in this scope
dvorakng.cpp:739: error: ‘KEY_BACKSPACE’ was not declared in this scope
dvorakng.cpp: In function ‘void boxed(int, int, char, char, char, int)’:
dvorakng.cpp:905: error: ‘A_REVERSE’ was not declared in this scope
dvorakng.cpp:905: error: ‘attron’ was not declared in this scope
dvorakng.cpp:910: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:910: error: ‘attron’ was not declared in this scope
dvorakng.cpp:915: error: ‘COLOR_PAIR’ was not declared in this scope
dvorakng.cpp:915: error: ‘attron’ was not declared in this scope
dvorakng.cpp:920: error: ‘move’ was not declared in this scope
dvorakng.cpp:921: error: ‘ACS_ULCORNER’ was not declared in this scope
dvorakng.cpp:921: error: ‘addch’ was not declared in this scope
dvorakng.cpp:922: error: ‘ACS_HLINE’ was not declared in this scope
dvorakng.cpp:925: error: ‘ACS_URCORNER’ was not declared in this scope
dvorakng.cpp:928: error: ‘ACS_VLINE’ was not declared in this scope
dvorakng.cpp:942: error: ‘ACS_LLCORNER’ was not declared in this scope
dvorakng.cpp:946: error: ‘ACS_LRCORNER’ was not declared in this scope
dvorakng.cpp:950: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp:958: error: ‘COLOR_PAIR’ was not declared in this scope
dvorakng.cpp:958: error: ‘attron’ was not declared in this scope
dvorakng.cpp:963: error: ‘A_REVERSE’ was not declared in this scope
dvorakng.cpp:963: error: ‘attroff’ was not declared in this scope
dvorakng.cpp:968: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:968: error: ‘attroff’ was not declared in this scope
dvorakng.cpp: In function ‘void show_layout(char, char)’:
dvorakng.cpp:1023: error: ‘refresh’ was not declared in this scope
dvorakng.cpp: In function ‘void myaddnstr(const char*, int)’:
dvorakng.cpp:1051: error: ‘addnstr’ was not declared in this scope
dvorakng.cpp: In function ‘UINT32 do_text(const char*, UINT32, THSManager&)’:
dvorakng.cpp:1074: error: ‘FALSE’ was not declared in this scope
dvorakng.cpp:1074: error: ‘curs_set’ was not declared in this scope
dvorakng.cpp:1076: error: ‘LINES’ was not declared in this scope
dvorakng.cpp:1076: error: ‘mvaddstr’ was not declared in this scope
dvorakng.cpp:1082: error: ‘move’ was not declared in this scope
dvorakng.cpp:1088: error: ‘refresh’ was not declared in this scope
dvorakng.cpp:1089: error: ‘noecho’ was not declared in this scope
dvorakng.cpp:1091: error: ‘getch’ was not declared in this scope
dvorakng.cpp:1093: error: ‘halfdelay’ was not declared in this scope
dvorakng.cpp:1096: error: ‘clrtoeol’ was not declared in this scope
dvorakng.cpp:1138: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:1138: error: ‘attron’ was not declared in this scope
dvorakng.cpp:1139: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp:1140: error: ‘attroff’ was not declared in this scope
dvorakng.cpp:1144: error: ‘ERR’ was not declared in this scope
dvorakng.cpp:1161: error: ‘KEY_BACKSPACE’ was not declared in this scope
dvorakng.cpp:1161: error: ‘KEY_DC’ was not declared in this scope
dvorakng.cpp:1171: error: ‘KEY_END’ was not declared in this scope
dvorakng.cpp:1179: error: ‘beep’ was not declared in this scope
dvorakng.cpp:1184: error: ‘flash’ was not declared in this scope
dvorakng.cpp:1215: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:1215: error: ‘attron’ was not declared in this scope
dvorakng.cpp:1221: error: ‘addch’ was not declared in this scope
dvorakng.cpp:1232: error: ‘attroff’ was not declared in this scope
dvorakng.cpp:1233: error: ‘A_REVERSE’ was not declared in this scope
dvorakng.cpp:1237: error: ‘addch’ was not declared in this scope
dvorakng.cpp:1247: error: ‘addch’ was not declared in this scope
dvorakng.cpp:1261: error: ‘clrtobot’ was not declared in this scope
dvorakng.cpp:1286: error: ‘clear’ was not declared in this scope
dvorakng.cpp:1300: error: ‘clear’ was not declared in this scope
dvorakng.cpp:1301: error: ‘cbreak’ was not declared in this scope
dvorakng.cpp:1305: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp:1307: error: ‘COLOR_PAIR’ was not declared in this scope
dvorakng.cpp:1307: error: ‘attron’ was not declared in this scope
dvorakng.cpp:1308: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:1322: error: ‘TRUE’ was not declared in this scope
dvorakng.cpp:1323: error: ‘echo’ was not declared in this scope
dvorakng.cpp: In function ‘void menuInteractive()’:
dvorakng.cpp:1337: error: ‘clear’ was not declared in this scope
dvorakng.cpp:1338: error: ‘refresh’ was not declared in this scope
dvorakng.cpp:1340: error: ‘COLOR_PAIR’ was not declared in this scope
dvorakng.cpp:1340: error: ‘attron’ was not declared in this scope
dvorakng.cpp:1341: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:1342: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp:1345: error: ‘attroff’ was not declared in this scope
dvorakng.cpp:1354: error: ‘move’ was not declared in this scope
dvorakng.cpp:1355: error: ‘clrtobot’ was not declared in this scope
dvorakng.cpp:1361: error: ‘echo’ was not declared in this scope
dvorakng.cpp:1363: error: ‘getnstr’ was not declared in this scope
dvorakng.cpp:1410: error: ‘getch’ was not declared in this scope
dvorakng.cpp: In function ‘int initColors()’:
dvorakng.cpp:1432: error: ‘start_color’ was not declared in this scope
dvorakng.cpp:1434: error: ‘has_colors’ was not declared in this scope
dvorakng.cpp:1440: error: ‘COLOR_BLUE’ was not declared in this scope
dvorakng.cpp:1440: error: ‘COLOR_BLACK’ was not declared in this scope
dvorakng.cpp:1440: error: ‘init_pair’ was not declared in this scope
dvorakng.cpp:1441: error: ‘COLOR_GREEN’ was not declared in this scope
dvorakng.cpp:1442: error: ‘COLOR_CYAN’ was not declared in this scope
dvorakng.cpp:1443: error: ‘COLOR_RED’ was not declared in this scope
dvorakng.cpp:1444: error: ‘COLOR_MAGENTA’ was not declared in this scope
dvorakng.cpp:1445: error: ‘COLOR_YELLOW’ was not declared in this scope
dvorakng.cpp:1446: error: ‘COLOR_WHITE’ was not declared in this scope
dvorakng.cpp: In function ‘void initApp()’:
dvorakng.cpp:1452: error: ‘window’ was not declared in this scope
dvorakng.cpp:1452: error: ‘initscr’ was not declared in this scope
dvorakng.cpp:1454: error: ‘COLS’ was not declared in this scope
dvorakng.cpp:1455: error: ‘LINES’ was not declared in this scope
dvorakng.cpp: In function ‘void closeApp()’:
dvorakng.cpp:1466: error: ‘move’ was not declared in this scope
dvorakng.cpp:1467: error: ‘clear’ was not declared in this scope
dvorakng.cpp:1468: error: ‘refresh’ was not declared in this scope
dvorakng.cpp:1469: error: ‘endwin’ was not declared in this scope
dvorakng.cpp: In member function ‘void TLessonManager::Menu()’:
dvorakng.cpp:1682: error: ‘noecho’ was not declared in this scope
dvorakng.cpp:1683: error: ‘FALSE’ was not declared in this scope
dvorakng.cpp:1683: error: ‘curs_set’ was not declared in this scope
dvorakng.cpp:1685: error: ‘clear’ was not declared in this scope
dvorakng.cpp:1686: error: ‘COLOR_PAIR’ was not declared in this scope
dvorakng.cpp:1686: error: ‘attron’ was not declared in this scope
dvorakng.cpp:1687: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:1689: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp:1703: error: ‘attroff’ was not declared in this scope
dvorakng.cpp:1711: error: ‘attroff’ was not declared in this scope
dvorakng.cpp:1736: error: ‘getch’ was not declared in this scope
dvorakng.cpp:1762: error: ‘echo’ was not declared in this scope
dvorakng.cpp:1763: error: ‘TRUE’ was not declared in this scope
dvorakng.cpp:1766: error: ‘getnstr’ was not declared in this scope
dvorakng.cpp:1805: error: ‘echo’ was not declared in this scope
dvorakng.cpp:1806: error: ‘TRUE’ was not declared in this scope
dvorakng.cpp:1809: error: ‘getnstr’ was not declared in this scope
dvorakng.cpp:1845: error: ‘echo’ was not declared in this scope
dvorakng.cpp:1846: error: ‘TRUE’ was not declared in this scope
dvorakng.cpp:1846: error: ‘curs_set’ was not declared in this scope
dvorakng.cpp:1847: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:1847: error: ‘attroff’ was not declared in this scope
dvorakng.cpp: In member function ‘void TLessonSlot::Show(UINT32, UINT32)’:
dvorakng.cpp:1878: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp: In member function ‘void TLessonSlot::Play()’:
dvorakng.cpp:1949: error: ‘clear’ was not declared in this scope
dvorakng.cpp: In member function ‘void THSManager::ShowScores()’:
dvorakng.cpp:1984: error: ‘FALSE’ was not declared in this scope
dvorakng.cpp:1984: error: ‘curs_set’ was not declared in this scope
dvorakng.cpp:1985: error: ‘cbreak’ was not declared in this scope
dvorakng.cpp:1986: error: ‘noecho’ was not declared in this scope
dvorakng.cpp:1987: error: ‘clear’ was not declared in this scope
dvorakng.cpp:1988: error: ‘refresh’ was not declared in this scope
dvorakng.cpp:1992: warning: deprecated conversion from string constant to ‘char*’
dvorakng.cpp:1996: warning: deprecated conversion from string constant to ‘char*’
dvorakng.cpp:1997: warning: deprecated conversion from string constant to ‘char*’
dvorakng.cpp:2000: warning: deprecated conversion from string constant to ‘char*’
dvorakng.cpp:2001: warning: deprecated conversion from string constant to ‘char*’
dvorakng.cpp:2004: error: ‘COLOR_PAIR’ was not declared in this scope
dvorakng.cpp:2004: error: ‘attron’ was not declared in this scope
dvorakng.cpp:2005: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:2006: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp:2007: error: ‘move’ was not declared in this scope
dvorakng.cpp:2010: error: ‘getch’ was not declared in this scope
dvorakng.cpp:2012: error: ‘echo’ was not declared in this scope
dvorakng.cpp:2013: error: ‘TRUE’ was not declared in this scope
dvorakng.cpp: In member function ‘void THSManager::ShowHistory()’:
dvorakng.cpp:2024: error: ‘clear’ was not declared in this scope
dvorakng.cpp:2025: error: ‘noecho’ was not declared in this scope
dvorakng.cpp:2026: error: ‘FALSE’ was not declared in this scope
dvorakng.cpp:2026: error: ‘curs_set’ was not declared in this scope
dvorakng.cpp:2028: error: ‘COLOR_PAIR’ was not declared in this scope
dvorakng.cpp:2028: error: ‘attron’ was not declared in this scope
dvorakng.cpp:2030: error: ‘window’ was not declared in this scope
dvorakng.cpp:2030: error: ‘getmaxyx’ was not declared in this scope
dvorakng.cpp:2036: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:2044: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:2044: error: ‘attroff’ was not declared in this scope
dvorakng.cpp:2045: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp:2046: error: ‘getch’ was not declared in this scope
dvorakng.cpp:2057: error: ‘echo’ was not declared in this scope
dvorakng.cpp:2058: error: ‘TRUE’ was not declared in this scope
dvorakng.cpp:2062: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:2062: error: ‘attroff’ was not declared in this scope
dvorakng.cpp:2063: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp:2064: error: ‘getch’ was not declared in this scope
dvorakng.cpp: In member function ‘void THSManager::ShowCharScores()’:
dvorakng.cpp:2178: error: ‘clear’ was not declared in this scope
dvorakng.cpp:2179: error: ‘noecho’ was not declared in this scope
dvorakng.cpp:2180: error: ‘FALSE’ was not declared in this scope
dvorakng.cpp:2180: error: ‘curs_set’ was not declared in this scope
dvorakng.cpp:2181: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:2181: error: ‘attron’ was not declared in this scope
dvorakng.cpp:2182: error: ‘COLOR_PAIR’ was not declared in this scope
dvorakng.cpp:2189: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp:2190: error: ‘getch’ was not declared in this scope
dvorakng.cpp:2198: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp:2210: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp:2214: error: ‘getch’ was not declared in this scope
dvorakng.cpp:2216: error: ‘TRUE’ was not declared in this scope
dvorakng.cpp:2217: error: ‘echo’ was not declared in this scope
dvorakng.cpp: In member function ‘void THSEntry::Print(UINT32, UINT32, UINT32, char*) const’:
dvorakng.cpp:2241: error: ‘A_BOLD’ was not declared in this scope
dvorakng.cpp:2241: error: ‘attroff’ was not declared in this scope
dvorakng.cpp:2242: error: ‘COLOR_PAIR’ was not declared in this scope
dvorakng.cpp:2242: error: ‘attron’ was not declared in this scope
dvorakng.cpp:2243: error: ‘mvprintw’ was not declared in this scope
dvorakng.cpp: In member function ‘void THSEntry::PrintHistory(UINT32) const’:
dvorakng.cpp:2282: error: ‘mvprintw’ was not declared in this scope
make: *** [dvorakng.o] Error 1
```

Honestly I don't understand where is the problem...:confused:
I'm using ubuntu Hardy 8.04.01 64bit

---

### Post by browndruid on 2009-03-15
If anyone can help with this, I'm having the same problem.

Thanks!

---

