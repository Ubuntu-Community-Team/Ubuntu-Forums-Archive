---
title: "VMplayer wont install"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by numberattic101 on 2010-12-16
i have tried

[https://sites.google.com/site/lightrush/random-1/vmwareplayeronubuntulucidormaverickrunningkernel2635](https://sites.google.com/site/lightrush/random-1/vmwareplayeronubuntulucidormaverickrunningkernel2635)

tom@tom-System-Product-Name:~/Desktop$ gksudo bash VMware-Player-3.4.1.3-324285.x86_64.bundle
VMware-Player-3.4.1.3-324285.x86_64.bundle: line 110: syntax error near unexpected token `newline'VMware-Player-3.4.1.3-324285.x86_64.bundle: line 110: `<html>'
ror near unexpected token `newline'tom@tom-System-Product-Name:~/Desktop$ 





[http://resalxh.wordpress.com/2010/09/09/vmware-player-3-1-1-on-ubuntu-10-10-maverick-meerkat/](http://resalxh.wordpress.com/2010/09/09/vmware-player-3-1-1-on-ubuntu-10-10-maverick-meerkat/)

tom@tom-System-Product-Name:~/Desktop$ chmod +x VMware-Player-3.4.1.3-324285.x86_64.bundle
tom@tom-System-Product-Name:~/Desktop$ sudo ./VMware-Player-3.1.1-282343.i386.bundle
sudo: ./VMware-Player-3.1.1-282343.i386.bundle: command not found
tom@tom-System-Product-Name:~/Desktop$ 

anyone know of a way to get this to work so i can install vmware player? Or know of a good virtual machine where graphics aren't so limited?

---

### Post by daqron on 2010-12-16
These version numbers don't match. Did you maybe copy/paste from the tutorial? Try sudo ./VM <tab> to autocomplete the filename so you don't have to worry about all the numbers.
> **numberattic101 said:**
> $ chmod +x VMware-Player-[COLOR="Red"]3.4.1.3-324285[/COLOR].x86_64.bundle
$ sudo ./VMware-Player-[COLOR="Red"]3.1.1-282343[/COLOR].i386.bundle

> **numberattic101 said:**
> Or know of a good virtual machine where graphics aren't so limited?

If it still doesn't work, VirtualBox OSE is in the repos. Easy install from the Ubuntu Software Center. I like it better but it still lacks USB support.

Good luck.

---

### Post by numberattic101 on 2010-12-17
ok i checked that and still not working. i tried vmbox before but the graphics was so low i couldnt use it for what i wanted. I use a virtual chat IMVU and need to run it in opengl or direct 9 so it wont chew up my cpu. Wine simple wont let those 2 options work. i own a copy of windows 7 and have it set to dule boot but want to get out of the rebooting to the other system.

is there a way to run windows on linux that would support the graphics of a virtual chat like imvu, or final fantasy 14(a bit extreme)?

---

### Post by daqron on 2010-12-18
Did you see this already? [http://ubuntuforums.org/showthread.php?t=1506685&page=2](http://ubuntuforums.org/showthread.php?t=1506685&page=2) The suggestion there was do a manual download instead of the VMWare download manager. And dumb question but you're definitely using a 64-bit system, right?

Have you looked into [PlayOnLinux]("http://wiki.winehq.org/PlayOnLinux") for gaming? Not a gamer myself so I don't really know anything, but if you can skip the VM you'd be in better shape for decent graphics performance.

---

### Post by numberattic101 on 2010-12-18
that was the issue thank you so much. was about to just give up and install windows then wubi ontop and hope it would work a lot better lol.

---

### Post by daqron on 2010-12-18
Excellent! Glad I could help prevent a windows install :)

---

