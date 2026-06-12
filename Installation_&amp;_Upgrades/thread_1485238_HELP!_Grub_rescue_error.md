---
title: "HELP! Grub rescue error"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by fawful on 2010-05-16
I had windows XP 64 bit professional edition installed. I then installed Ubuntu 9.10 in windows from a CD. I was soon asked to upgrade to 10.04. During the upgrade it asked which drives to install grub to. Wasn't sure which one to choose so followed help message and clicked on all of them. When computer restarted it came up with a message 

error: no such device: e6a2da2b-c868-4c49-b4a8-6b3157de2b4d
grub rescue>

I am new to Ubuntu and dont have a clue what to do. Please help. It wont let me get into ubuntu or windows. Thanks in advance

---

### Post by surfwy22 on 2010-05-17
I am an absolute newbie and am running into the same issue.  You might/should be able to boot from the installation disc.  
1) put install disc in drive
2) start machine
3) when first screen opens (mine is pink/purple) with two symbols at the bottom of the screen hit F8
4) you should be prompted with a menu with the last choice being "Boot from Local Disc" - highlight this option and hit enter
5) give your machine a minute and you should be shown a black screen with a list of operating system options - pick the most recent ubuntu install (probably the top)
6) May take a minute but you should be good.

Others who may read this:
when I enter ls from the grub rescue prompt I get (HD0) (HD0,2) (HD0,1) - I'm looking for the X,Y values to boot from Grub Rescue prompt - what values am I looking for?
IBM Thinkpad CD install

---

### Post by oldfred on 2010-05-18
Welcome to the forums:
surfwy22 since your results.txt will be totally different please start your own thread and post the results there.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to select/highlight and use code tags ([COLOR=Black]#[/COLOR] in right side of edit panel above as you paste results.txt) to make it easier to read when you post the results.txt.

If you installed grub every where you should be able to boot, but if not you may have to reinstall grub. You may also have problems with windows. The above report will tell us what to do next.

---

