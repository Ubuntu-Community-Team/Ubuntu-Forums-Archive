---
title: "xserver-xfree"
date: 2004-11-12
forum: Installation &amp; Upgrades
---

### Post by ReddoC on 2004-11-12
Is someone has a problem to install xserver-xfree86 ?! i have already installed many 
others distrib with no problem ! even with kernel 2.6.8 (suse9.2, Kanotix live cd, ....) And i can't get over this problem with ubuntu.

My problem is when I install xfree-xserver86, the preconfiguring script is blocking.

I can wait 30 minutes and nothing happend. What can be the problem .

Help !

---

### Post by Jos Walrave on 2004-11-12
First search for already [ posted messages]( http://ubuntuforums.org/search.php?searchid=33074) on this subject!  :evil:

---

### Post by cseg on 2004-11-12
[QUOTE=Jos Walrave]First search for already [ posted messages]( http://ubuntuforums.org/search.php?searchid=33074) on this subject!  :evil:[/QUOTE]How does "Sorry - no matches. Please try some different terms" help?

---

### Post by ReddoC on 2004-11-13
[QUOTE=Jos Walrave]First search for already [ posted messages]( http://ubuntuforums.org/search.php?searchid=33074) on this subject!  :evil:[/QUOTE]


Anything ! I  have tried to search since one week. and can't find any answer.

So I have to think tha Ubuntu is not as good as the community say, OR I have to think that this good community would help me and in the same time, a lot of people with this problem.

---

### Post by HiddenWolf on 2004-11-13
[QUOTE=Jos Walrave]First search for already [ posted messages]( http://ubuntuforums.org/search.php?searchid=33074) on this subject!  :evil:[/QUOTE]

Dude, that is no way to help, before you give such a comment, actually make sure that the awnser is already there. At least provide a link to a howto/wiki/post to be of any help.

This, imho just falls into the 'read the f manual' attitude, which is exactly the reason why I ditched debian.

---

### Post by HiddenWolf on 2004-11-13
To Reddoc, could you provide any info, some logs, anything?
You don't really provide a handle for me to go about and help you find a solution.

---

### Post by ReddoC on 2004-11-13
[QUOTE=HiddenWolf]To Reddoc, could you provide any info, some logs, anything?
You don't really provide a handle for me to go about and help you find a solution.[/QUOTE]

The only thing i can tell, it this:

i type this command:
> apt-get update
> apt-get install xserver-xfree86
the package is being downloaded, then it 's writing : preconfiguring ...

and then nothing else. How can i know what the script is doing ? 

How, where could i find a log to give you ?


Thanks for your help.

---

### Post by Razvan on 2004-11-13
it happened to me too on a acer laptop, when he stopped at xfree, the other packages are still in aptitude so i just zold aptitude to install all the selected and - good thing - it installed xfree too.

then just run base-config again and it will configure

cheerz

---

### Post by HiddenWolf on 2004-11-13
that might very well fix it.

---

### Post by daniels on 2004-11-13
Looks like discover is failing; I've seen this happen a couple of times for no good reason when probing the USB bus (kernel reads just hang), so I'll upload xorg sometime next week that disables probing the USB bus also.

---

### Post by ReddoC on 2004-11-14
[QUOTE=daniels]Looks like discover is failing; I've seen this happen a couple of times for no good reason when probing the USB bus (kernel reads just hang), so I'll upload xorg sometime next week that disables probing the USB bus also.[/QUOTE]


I have already tried with aptitude, but it block again with xserver-xfree86.

maybe is th usb bus ?! .. i 'll try with xorg. But Where can i get it ?

ReddoC

---

### Post by ReddoC on 2004-11-16
I have tried to make a dist-upgrade.

but when finished, xorg wasn't installed. so i make a sudo apt-get install xserver-xorg and i download it and it block on -> dpkg-preconfigure --apt

as with xserver-xfree86 !!

---

### Post by ReddoC on 2004-11-17
[QUOTE=ReddoC]I have tried to make a dist-upgrade.

but when finished, xorg wasn't installed. so i make a sudo apt-get install xserver-xorg and i download it and it block on -> dpkg-preconfigure --apt

as with xserver-xfree86 !![/QUOTE]



Ok i have found why it was blocking. I had to stop my usb bus from the bios. install Xfree86 or xorg and then enable my usb bus (from the bios).

Thank for your help !

ReddoC

---

