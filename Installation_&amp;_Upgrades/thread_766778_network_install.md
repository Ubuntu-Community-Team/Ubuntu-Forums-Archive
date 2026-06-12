---
title: "network install"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by ziofil on 2008-04-25
hi everybody! :)
I have a little installation issue, it will be a silly thing for you geeks, but for me it's still quite tricky..
i have a benq laptop which has no cdrom drive (it is external, but it is broken...:(), with windows in it, and i want to get rid of that crappy os..! so i decided to perform a network install, since i have a fully working pc with ubuntu hardy already running and a fresh xubuntu hardy cdrom. 
i read some threads, but they all say to select 'network install' and write the ip address of the machine in which i have to install hardy, but what ip do i insert? do i have to let it turn on with windows and insert the ip that the router assigned to it? i'm afraid of messing things up.. :(
any help would be very appreciated! thank you in advance!:KS

---

### Post by Pumalite on 2008-04-25
Change last octect from the one assigned to Windows

---

### Post by dstew on 2008-04-25
Assuming that your notebook has a PXE BIOS, you don't need to assign an IP address if you use DHCP instead of bootp. That is, you set up your Linux box as the local network's DHCP server instead of your router, and when your notebook boots, its BIOS sends a DHCP request out to the network even before Windows boots. The DHCP request gets answered by your Linux DHCP server, and then your notebook asks the Linux box for a kernel image to boot (that is the special PXE part). The Linux box sends it a kernel image by tftp, and the notebook boots it. Then, running that kernel, you get an installation menu. I did this to install over the Internet instead of using a local image, but the overall technique is the same. See my experience [here]("http://ubuntuforums.org/showthread.php?t=690483").

---

### Post by ziofil on 2008-04-25
by 'last octect' you mean the last number of the ip? wouldn't it be pointing somewhere else then?

sorry if i seem so dumb :(, but i understood the procedure to be:
1- turn on ubutnu on the pc
2- turn on windows on the laptop
3- select network install on the cdrom on the ubuntu machine
4- write the ip of the windows machine (which is still running) on the network install prompt (eventually changing the last octect, that i don't know what it is :confused:)
5- let it do all the work
?

---

### Post by ziofil on 2008-04-25
> **dstew said:**
> Assuming that your notebook has a PXE BIOS, you don't need to assign an IP address if you use DHCP instead of bootp. That is, you set up your Linux box as the local network's DHCP server instead of your router, and when your notebook boots, its BIOS sends a DHCP request out to the network even before Windows boots. The DHCP request gets answered by your Linux DHCP server, and then your notebook asks the Linux box for a kernel image to boot (that is the special PXE part). The Linux box sends it a kernel image by tftp, and the notebook boots it. Then, running that kernel, you get an installation menu. I did this to install over the Internet instead of using a local image, but the overall technique is the same. See my experience [here]("http://ubuntuforums.org/showthread.php?t=690483").

Oh, that seems reasonable! :)
thanks a lot, i'll try!
then i'll post the results and hopefully mark the thread with a solved sign!

---

### Post by Pumalite on 2008-04-25
Sorry, I had my head in the moon.

---

### Post by ziofil on 2008-04-26
no problem ;)
Anyway i managed to get a working external usb cdrom drive, so i'm afraid i'll try the network setup another time!
thank you all

---

