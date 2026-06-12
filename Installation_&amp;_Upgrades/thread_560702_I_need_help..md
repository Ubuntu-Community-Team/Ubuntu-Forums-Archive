---
title: "I need help."
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by ggomez on 2007-09-26
I'm very new to Linux and after many years dealing with Windows with my old job I got a great new job that likes to run Linux servers and desktop. So I decided to that the best way for me to catch up is to make a new Linux desktop using Ubuntu. I downloaded Ubuntu 7.04 Live CD, no luck. I read the forums and got the alternative CD, that didn't work. I thought maybe Ubuntu 7.04 wasn't working for my computer so I get 6.06 that doesn't work. Here are my specs to the computer I'm making.

ASUS M2A-VM AMD Socket AM2 Athlon 64 X2 
Athlon x2 4200+ AM2
320 GB SATA
2 GB DDR2800

I really need step by step instruction on what to do. I read the other forums and feel like I try to understand what there saying but I don't.

This is what happens when I try installing Ubuntu 6.06, I choose "Start or Install Ubuntu" then the loading happens on top of the screen. After a few seconds it tries to go into the next step and the computer reboots itself starting the process all over again. This didn't happen with 7.04 instead I was getting this "can't access tty; job control turned off" But I found this post 
[http://ubuntuforums.org/showthread.php?t=559863&highlight=sata]("http://ubuntuforums.org/showthread.php?t=559863&highlight=sata")

that didn't help so that when I decided to try 6.06 first then update to 7.04 after I got it working but I can't.
Like I said I need step by step instruction on what I should do from the beginning. [SIZE="3"][COLOR="black"]**I can't wait to make this finally work!!**[/COLOR][/SIZE]

---

### Post by rsambuca on 2007-09-26
A few questions:

Did you check the md5sums of the iso's that you downloaded to ensure integrity?
Did you burn the iso's a slow speed to avoid errors?
Did you run the CD check (if you can get that far)?
What is your videocard?

---

### Post by ggomez on 2007-09-26
thank you for the reply!!!
So I ran the CD check and I got this 

Decompressing Linux....done.
Booting the kernel.
[ 2178.865936] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[ 2179.115351] <0>Kernel panic - not syncing: Aiee, killing interrupt handler!>
 idle+150}+0}hread_return+0}pt+57}}

---

### Post by Pumalite on 2007-09-26
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by ggomez on 2007-09-26
Thanks for the reply I will try that thanks. Going home to sleep I will try this tomorrow.

---

### Post by ggomez on 2007-09-27
So I followed the instructions provided by Pumalite and I get this error after preforming the CD check.
Decompressing Linux....Ok, booting the kernel.
[ 17179569.764000] ...MP-BIOS bug: 8254 timer not connected to IO-APIC
[ 17179570.152000] PCI: Cannot allocate resourses region 1 of device 0000:00:14.0

---

### Post by Pumalite on 2007-09-27
Did you try the Alternate CD? If yes, then clean the lens in your burner, try the CD's in another computer,etc.

---

