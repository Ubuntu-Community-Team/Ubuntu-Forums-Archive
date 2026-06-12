---
title: "Printer install"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by andycc55 on 2013-04-29
I have just upgraded to ubuntu13.04 I cannot get my  canon pixma ip1900 to install have tried just about every thing and I am getting very frustrated I get this message after following the recommendations CUPS server error There was an error during the CUOS operation:'client-error-documentation-format-not supported I also noteiced no drivers for my particular printer yet there are for other models I'm getting very frustrated

can  any one help ? please ?

ta

---

### Post by Cheesehead on 2013-04-29
How did you install your printer before?
Software Center? web site? manufacturer CD?

How did you upgrade?
For example, if you 'upgraded' by reinstalling, then of course all previous installs were wiped...

---

### Post by pdc on 2013-04-30
you must be very frustrated and exasperated Andy;

you don't mention if you have 32bit or 64bit Ubuntu installed;

with 32bit, Canon supply [COLOR="#0000FF"].deb[/COLOR] packages that should get the ip1900 going well; 

for 64bit, you will need some symbolic links as well as the Canon drivers; (the symbolic links tell your system to look in lib64 whereas the drivers will think only to look in lib ............)

Canon supplies two packages;

1) install the [COLOR="#EE82EE"]common package[/COLOR] first: get it from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100159003.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100159003.html) and it comes down as [COLOR="#008000"]cnijfilter-common_3.00-1_i386.deb[/COLOR] so as you click to download [COLOR="#0000FF"]gdebi installer[/COLOR] should offer to install ......accept its kind offer .....

2) install the [COLOR="#EE82EE"]ip1900 package[/COLOR]: go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100159101.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100159101.html) and download the [COLOR="#008000"]cnijfilter-ip1900series_3.00-1_i386.deb[/COLOR] ..again let [COLOR="#0000FF"]gdebi installer[/COLOR] do the work ............

let us know whether you have 32bit or 64bit

---

