---
title: "Usb Cd Rom"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by 2j4ez on 2006-10-04
Hello all my first post so here goes
my friend keeps going at me about ubuntu and how great it is so i downloaded it and want to try it

run into a problem cannot install it on my laptop with usb cd rom (got rid of my desktop for apple :-D )

the installer loads up ok but it cannot dectect any CD rom drives Because the cd rom is on USB

any ideas on how to get the installer to work with a usb cd rom??

please help  
can some one send me the link for ubuntu live 

thanks for your time

---

### Post by Kateikyoushi on 2006-10-04
Which version are you trying to install ?

You can get the live cd here, choose desktop after selecting a download site.
[Download ubuntu]("http://www.ubuntu.com/download/").

The live version worked with my firewire dvd writer so should work with usb as well. In case it can boot but the installer can't find the cd you might have to add options at boot, in my case with another distro there were acpi=on doscsi dofirewire.

---

### Post by 2j4ez on 2006-10-04
ununtu 6.06.1 I386 is the one i am trying to install will look for the live CD and download that and try and run it

the one i downloaded earlier doesent seem to be the live downloading the live cd now

---

### Post by Kateikyoushi on 2006-10-04
The link name should be: PC (Intel x86) desktop CD.
This is a live cd iso filename: ubuntu-6.06.1-desktop-i386.iso

---

### Post by 2j4ez on 2006-10-04
downloading it now can i install it from the live CD??

---

### Post by Kateikyoushi on 2006-10-04
Yes there is an install icon on the desktop which starts the installer.

---

### Post by 2j4ez on 2006-10-04
it did not work it loads up about half way then it says the usb device is not accepting address 4,error 110

---

### Post by Kateikyoushi on 2006-10-04
Seems to me you ran into this bug : [Link.]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/54273")

---

### Post by 2j4ez on 2006-10-04
anyway to cure it??

---

### Post by plut0nium on 2006-10-27
I had exactly the same problem on my laptop...

I switched to a console (CTRL-ALT-F2) and mounted the drive manually (mount /dev/scd0 /cdrom) and then just switched back to the installer and skipped the cd-ron detection step...

it worked perfectly...

---

