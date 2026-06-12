---
title: "cups-pdf problem after intrepit upgrade"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by ribico on 2008-11-03
Hi all,
I have recently upgraded to Intrepid and I discovered that cups-pdf was not more available in printers..
Since it is useful for many reasons I wanted to have it back working even if in some cases "print to file" function can help.

after some googling I realized that cups-pdf package was not more installed and I installed it again.

Then I saw the printer and it seemed to work.. but files were produced nowere.

Here is my system configuration:

## permissions of my printer backend:
-rwx------ 1 root root 22888 2008-06-23 17:39 /usr/lib/cups/backend/cups-pdf

## my out directory as specified in /etc/cups/cups-pdf.conf
Out ${HOME}/PDF

## permissions of the output directory:
drwxrwxrwx 2 gabriele gabriele 4096 2008-10-31 18:06 /home/gabriele/PDF

## /etc/apparmor.d/usr.sbin.cupsd cups-pdf related lines
# we treat cups-pdf specially, since it needs to write into /home
# and thus needs extra paranoia
/usr/lib/cups/backend/cups-pdf Px,
 
Any advice ?

thanks
- gabriele

---

### Post by kaibob on 2008-11-04
You may want to look at post 12 in the following thread:

[http://ubuntuforums.org/showthread.php?t=626718&page=2](http://ubuntuforums.org/showthread.php?t=626718&page=2)

I couldn't get cups-pdf to work with the default settings, but it began working after I changed the PDF folder as directed in referenced post. Perhaps a bit of a long shot, but it may be worth a try if nothing else helps.

---

### Post by ribico on 2008-11-04
Thanks kaibob,
I've already tried that.. but no helps.

Any other advice ?

---

### Post by sqrooup on 2008-11-04
Try this;
go to Terminal, and input [I]sudo /etc/init.d/cups restart
[/I]
Hope this helps

(Note the wiki tells you to use *sudo /etc/init.d/cupsys restart*, but the *cupsys* has been renamed *cups* in Heron and Ibex!)

---

### Post by kaibob on 2008-11-04
> **ribico said:**
> Thanks kaibob, I've already tried that.. but no helps. Any other advice ?

Not really except to look at the cups-pdf threads in the Intrepid beta forum. For example, see post 12 in the following:

[http://ubuntuforums.org/showthread.php?t=947960&page=2](http://ubuntuforums.org/showthread.php?t=947960&page=2)

Some people had trouble after installing cups-pdf in Intrepid, and no explanation for this was ever found. Sorry I couldn't be of more help.

---

### Post by ribico on 2008-11-05
Thanks to all..
but I've tried both cups restart and backend permissions.. no luck.

---

### Post by callan79 on 2008-11-05
> **ribico said:**
> Thanks to all..
but I've tried both cups restart and backend permissions.. no luck.


Just been having the same problem, but it seems that instead of a PDF printer, you now just use the 'print to file' option.

Refer [http://ubuntuforums.org/showthread.php?t=966272&highlight=cups-pdf](http://ubuntuforums.org/showthread.php?t=966272&highlight=cups-pdf)

The PDF printers that I created don't work, but print to file then choose PDF worked fine.

Cheers
Callan

---

### Post by ribico on 2008-11-07
Did you see it is not the same thing ?
Print to file function is not available for all the programs.. wile cups-pdf can be used as a standard printer..

ciao

---

### Post by pnavarrc on 2008-11-12
Hello,

   I installed the cups-pdf package, and doesn't work either. I try some potential solutions (the post 12), and finally, i manage to make the PDF printer work:

Go to System > Administration > Printing

In the window "Printer configuration - localhost", go to "Server" > "Connect" and change to "/var/run/cups/cups.sock". After this, I was able to printo to PDF as usual (without change my PDF folder). I hope that helps,

   Pablo.

---

### Post by ribico on 2008-11-13
It doesn't seem to work for my system.

ciao
- gab

---

### Post by dinarcon on 2008-11-23
hi ribico,

You've got to create a "PDF" directory in your home folder. This is how I overcome the problem:

1.- Go to "System -> Administration -> Synaptic Package Manager"
2.- Search and install "cups-pdf"
2.1.- I read that "cups-driver-gutenprint" has to be installed as well. In my case, it was already installed.
3.- [by [stinger30au]('http://ubuntuforums.org/showthread.php?t=983808')] Go to your home directory and create a folder named "PDF" (all letters capitalized)

after doing so, and without further configuration, I was able to print to PDF!

The same can be done at the command line as follows:
1.- "sudo apt-get install cups-pdf"
2.- "mkdir ~/PDF"

note: I tried other options before doing as indicated above. One of them (as suggested by [aggiemarine07]('http://ubuntuforums.org/showpost.php?p=6216706&postcount=18')) was using this command:
"sudo chmod 0755 /usr/lib/cups/backend/*"
...not quite sure if it helped as well.

(remark: aggiemarine07 did not include sudo as part of the command, but if not present I hadn't permission to modify the files' attributes)

---

### Post by petzler on 2008-11-29
I'm concern as well. As far I did read the problem is related to appamor. The obviosly solution to create ~/PDF dir doesn't work therefore. Hopefully this be fixed next time. As a work around I disable appamor temporary by /etc/init.d/appamor {stop|start} as I'm root of my box.

Regards,
Olaf

---

### Post by ribico on 2008-12-01
petzler finally you hit the ball !
AppArmor seems to be the problem in my system too.. great hint.

Hope it will be solved soon, do you think it is "dangerous" to work with AppArmor stopped ?

---

### Post by ribico on 2008-12-01
you know what ?
I have also modified my /etc/apparmor.d/usr.sbin.cupsd and /etc/cups/cups-pdf.conf to let it print in Desktop as showed at this link [http://ubuntuforums.org/showthread.php?t=626718&page=2](http://ubuntuforums.org/showthread.php?t=626718&page=2)

but it didn't help..
the only solution for me is to stop apparmor.

---

### Post by petzler on 2008-12-02
The above work around does not work since/starting with 8.10 :(

I've no idea what changed but following the entries in diverent forums: cups on intrepid is a mess now (got never problems on 8.04 - long term support ):P ).

Anyway, appamor saves your home directory on amok running apps (e.g. maybe by an hijacked browser ...). You can sleep better on enabled appamor. A disabled appamor decreases the security a little bit. If you print a lot using cups-pdf personaly I would permanent disable appamor - since I use it seldom I disable it only temporary.

Regards,
Olaf

---

