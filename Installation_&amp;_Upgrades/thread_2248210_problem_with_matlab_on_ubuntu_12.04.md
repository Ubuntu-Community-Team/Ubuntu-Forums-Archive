---
title: "problem with matlab on ubuntu 12.04"
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by michal11 on 2014-10-13
i must united library EhterLab and Matlab 2012b and i follow instructions : 
> [COLOR=#444444][FONT=Verdana]Regardless whether you install using a package manager or from source [/FONT][/COLOR]
[COLOR=#444444][FONT=Verdana]code, the package has to be configured to work with MATLAB . [/FONT][/COLOR]

[COLOR=#444444][FONT=Verdana]Start MATLAB, and call setup: [/FONT][/COLOR]
[COLOR=#444444][FONT=Verdana]>> run /opt/etherlab/rtw/setup_etherlab.m

and i have little problem with configuration because, one file not found.

```
[/FONT][/COLOR][COLOR=#000000][FONT=Courier] [/FONT][/COLOR][COLOR=#000000][FONT=Courier]run /home/michal/vol/opt/etherlab/src/etherlab-2.1.0/rtw/setup_etherlab.m [/FONT][/COLOR]
[COLOR=#000000][FONT=Courier][IMG]http://www.matlab.pl/images/nums/2.png[/IMG][/FONT][/COLOR][COLOR=#000000][FONT=Courier]EtherLAB search directories are already in $MATLABPATH [/FONT][/COLOR]
[COLOR=#000000][FONT=Courier][IMG]http://www.matlab.pl/images/nums/3.png[/IMG][/FONT][/COLOR][COLOR=#000000][FONT=Courier]Precompiling functions in /home/michal/vol/opt/etherlab/src/etherlab-2.1.0/rtw/blocks [/FONT][/COLOR]
[COLOR=#000000][FONT=Courier][IMG]http://www.matlab.pl/images/nums/4.png[/IMG][/FONT][/COLOR][COLOR=#000000][FONT=Courier]/usr/bin/ld: cannot find -lstdc++ [/FONT][/COLOR]
[COLOR=#000000][FONT=Courier][IMG]http://www.matlab.pl/images/nums/5.png[/IMG][/FONT][/COLOR][COLOR=#000000][FONT=Courier]collect2: ld returned 1 exit status [/FONT][/COLOR]
[COLOR=#000000][FONT=Courier][IMG]http://www.matlab.pl/images/nums/6.png[/IMG][/FONT][/COLOR][COLOR=#000000][FONT=Courier] [/FONT][/COLOR]
[COLOR=#000000][FONT=Courier][IMG]http://www.matlab.pl/images/nums/7.png[/IMG][/FONT][/COLOR][COLOR=#000000][FONT=Courier]    [/FONT][/COLOR][COLOR=#000000][FONT=Courier]mex: link of ' "world_time.mexa64"' failed. [/FONT][/COLOR][COLOR=#444444][FONT=Verdana]
```
[/FONT][/COLOR]

---

### Post by steeldriver on 2014-10-13
Hello and welcome to the forums

It looks like that particular matlab file is trying to compile some stuff using mex / C++

It's been a while since I played with mex, but at the least you will need a C/C++ development environment installed on your machine - you can do that by installing the build-essential metapackage

There may be other hoops to jump through (such as configuring your matlab installation to recognize the GNU compiler)

---

