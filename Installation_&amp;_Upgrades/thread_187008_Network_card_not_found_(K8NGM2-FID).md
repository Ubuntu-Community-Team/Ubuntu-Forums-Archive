---
title: "Network card not found (K8NGM2-FID)"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by awarberg on 2006-06-02
Hi

I just installed the new Ubuntu. I'm impressed by how easy and quickly the installation went, good job! 

Unfortunately it seems that it failed to find my network card (onboard 'NVIDIA nForce Network Controller') in my desktop computer. 
In System -> Administration -> Networking I do have an eth0 adapter which can be enabled and disabled. However I can see that no DHCP information is retrieved and the DNS servers are not discovered (this works in Windows). Furthermore, enabling the adapter after disabling it takes a long time (~1 min.).

How do I proceed to get online?

Another problem is that my GeForce 6150 (integrated) video card is not detected correctly. At least I'm not allowed to switch to my screens native resolution (1280x1024); I'm limited to 1024*768. This is a bit odd since the hardware support sites claim that the geforce 6 integrated series is automatically discovered.

I hope you can help me on these issues.

Best regards
Andreas

Ps. FYI I've installed the ubuntu-6.06-desktop-i386 on my AMD X2 system. I believe this shouldn't be a problem (again, it works on Windows).

Update: I just installed ubuntu from the same dvd on my laptop (Dell Inspiron 8200) and everything seems fine. The DHCP thing too.

---

### Post by John.Michael.Kane on 2006-06-02
awarberg I had looked into buying this board at one time, and was told that VITESSE VSC8201RX which the FID uses for lan was not supported on every distro (Fedora Core 5) has been said to work with this board.

---

### Post by awarberg on 2006-06-03
So does this mean I should forget about getting it to work? Btw. I installed the amd64 version which didn't help on my problem. 

The eth0 is there but no dhcp info is received. The command sudo dhcpclient show a lot of broadcasts but no responses.

---

### Post by John.Michael.Kane on 2006-06-03
awarberg if you can would you mind testing  fedora core 5 to see if it sees your etho.  all the searching i did shown ubuntu not supporting this network chip.

---

### Post by awarberg on 2006-06-03
I would rather avoid having to download and burn the 5-something cd set for fedora core 5 since I'm on a slow line and I have to get some work done too. Is there some way to simply install the correct drivers?

Regards
Andreas

---

### Post by John.Michael.Kane on 2006-06-03
At this time I know of no way to get it working under ubuntu. like i said everything i read seems to be that the board works well under other distros but this one. 

sorry i could not be of more help on this subject.



**Sidenote**: If there are any users of this board that have got the networking, and video sorted out under **Ubuntu** please post here..
Thank you.

---

### Post by Jacques Bloyard on 2006-06-03
I have the MSI K8NGM2-FID and I can tell you that the built in nVidia NIC does function with Dapper 6.06. I must confess that during the initial install with the Alternate disc it simply would not function and I ended up putting an Intel NIC to  download the stuff I needed to get everything functionning. Once that was done I decided to have another go at getting the nVidia NIC working. I went into the BIOS to re-enable the Mac Lan and on a hunch I decided to disable the Mac Lan bridge (it is enabled by default). I booted back up and went to system/admin/networking and pressed the activate button. The NIC activated immediately, which was not the case before, and Firefox hooked up to the internet immediately. I then removed the Intel NIC.

About the built in video chip I cannot comment since I use an ATI X1600XL. I had to use method #2 to load the ATI driver to get decent hardware acceleration.

---

### Post by John.Michael.Kane on 2006-06-03
Jacques Bloyard thanks for the info.

---

### Post by Belarios on 2006-06-03
If you are dual booting with Windows, try unplugging the power cord from the back of the computer for 15 seconds and then restoring it and booting into linux (without booting into Windows first).

If that solves your problem, check here:

[http://ubuntuforums.org/showthread.php?p=1083320#post1083320](http://ubuntuforums.org/showthread.php?p=1083320#post1083320)

---

