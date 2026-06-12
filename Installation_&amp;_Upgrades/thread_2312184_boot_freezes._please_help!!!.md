---
title: "boot freezes. please help!!!"
date: 2016-02-02
forum: Installation &amp; Upgrades
---

### Post by Francisco_Abarquer on 2016-02-02
hi,
i´m kind of new with lubuntu.
i have it installed for a while but just follow web tips or instructions to install and/or mess around with it on a user level, i tried to install POPCORN-TIME... couldnt do it at first, so i checked on the web... type few comand lines... still fail... so forget about it... keep running my computer for a while... turn off... NEVER boot properly again... starts... freezes... i runned "boot-repair", and didnt fix it but gave this url: [COLOR=#0000ff]http://paste.ubuntu.com/14859938/[/COLOR] all seems to have to do with 
[COLOR=#ff0000]error while loading shared libraries: libudev.so.1: cannot open shared object file: No such file or directory

[/COLOR][COLOR=#000000]please help, i can reach recovery mode but dont know what to do... and dont want to make it worse... thanks!!![/COLOR][COLOR=#ff0000] 
[/COLOR]

---

### Post by kansasnoob on 2016-02-03
A link to the web page you followed for running those commands would be helpful. Without that info we're blind as to what may have caused the problem. Best guess is that X is now broken, but that's a guess and only a guess.

---

### Post by Francisco_Abarquer on 2016-02-03
well, first thanks for answering... second, all i typed as i can remember, the pages i really dont, is something like [COLOR=#ff0000]sudo ln -s -f /lib/i386-linux-gnu/libudev.so.1 /usr/lib/libudev.so.0

[/COLOR][COLOR=#000000][/COLOR][COLOR=#000000]i  really dindt meka the Popcorn app work, so as i mentioned, i kept using  my comuter normally, is when i switched off and back on that this  happened... hopefully this little info may help to find a solution, I´m  sure it cant be anything very critical... thanks[/COLOR][COLOR=#000000][/COLOR]

---

### Post by kansasnoob on 2016-02-03
That may be why Boot Repair complains:

> error while loading shared libraries: libudev.so.1: cannot open shared object file: No such file or directory

But there are two additional errors reported by Boot Repair:

> cat: /tmp/boot-sav-VsdA3/1.tee: No such file or directory

> /usr/sbin/grub-probe: error while loading shared libraries: libudev.so.1: cannot open shared object file: No such file or directory

The first and the last are probably due to creating a symlink as shown by that command (I think but I'm really out of my depth here).

Why it's complaining about no /temp I have no idea :redface:

---

### Post by Vladlenin5000 on 2016-02-03
Similar errors have been reported with failed attempts to install Spotify. Apparently it's a typical unresolved dependencies problem. 

Popcorn Time is dead since some time ago and it's **illegal** pretty much anywhere in the western world - it provides easy access to copyrighted media contents - and in some EU country the local authorities even indicted a couple of teens for nothing more than blog posts with some sort of tutorial for the aforementioned software.

I suggest you install **ppa-purge** and use it to remove all traces of anything that might have come from the PPA that broke your system.

---

### Post by Francisco_Abarquer on 2016-02-03
thank you, ou grazinhas... i dont know about ppa-purge... can you tell me how to work it out?? i can only acces the computer on recovery mode with no access to the web straigt from it... thank you again...

---

### Post by Vladlenin5000 on 2016-02-03
[http://www.ubuntubuzz.com/2012/02/newbie-guide-how-to-use-ppa-purge.html](http://www.ubuntubuzz.com/2012/02/newbie-guide-how-to-use-ppa-purge.html)

Replace the example PPA for the one you added for Popcorn and hope for the best...

PS - Lovely detail, "grazinhas"... I'm really touched by this and the mix of the two concurrent spellings was really funny :-)

---

### Post by Francisco_Abarquer on 2016-02-05
hi again, since i dont have access to internet from that computer... is there any other way to fix my boot? i can run a live LXLE sesion from usb and then get my wifi on... maybe i can do something from there?? i´m quite lost...
 Graziñas, eu te escribo en ingles por que e mais fazil ke outros usuarios podan entender a miña pregunta... un saudo

---

### Post by Francisco_Abarquer on 2016-02-06
HELP!!!!
can someone out there help me??

---

### Post by Vladlenin5000 on 2016-02-06
> **Francisco_Abarquer said:**
> hi again, since i dont have access to internet from that computer... 

Oh, big problem...
Well, assuming the freeze happens after trying to log in then you can try a "command line" mode -> CTRL+ALT+F1 <- and, with an ethernet cable connected, log in by typing the username then password... At this point you should be able to install and use ppa-purge (you need the exact name of the PPA as shown in the example). If you tried [this instructions]("http://www.comoinstalarlinux.com/como-instalar-popcorn-time-desde-un-ppa-en-ubuntu-y-linux-mint/"), now use the same name "ppa:..."

Obs.: I *think* you don't need to have internet to use ppa-purge, unless some files need to be downloaded again. The purpose of ppa-purge is twofold: a) remove a PPA from software sources and b) revert any actions from that PPA. It most likely will be able to do this with internet connection just by uninstalling the PT software but it all depends on what other files have been changed when you tried to install it (ppa-purge should be able to revert to the previous versions but if not, it'll need to obtain those files from the online repository).

---

