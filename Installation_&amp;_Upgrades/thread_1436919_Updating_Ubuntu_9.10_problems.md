---
title: "Updating Ubuntu 9.10 problems"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by naru2bon on 2010-03-23
Sorry guys, I'm new to linux, forgive the ignorance, I'm just learning, i need your help, I installed ubuntu 9.10 on my 4gb Sandisk Cruzer flashdrive and updated it via updates interface. It finished all the downloading of updates and i think its about halfway installing the updates, as it shows "replacing openoffice.org" something then the screen went blank, i thought it went to a power saver mode because maybe i'm not touching anything but then i tried pressing my keyboard and it showed a box asking for a password. I tried pressing login without entering anything which gives me authentication failure, then i leave it for another 30mins thinking it might still be applying the changes in the background but nothing happens and the screen is just blank, pressed the keyboard again but this time it only showed the "loading circle" icon so i gave it another 30mins (boy i'm patient) then pressed the keyboard and this time around i'm only seeing the cursor on a black screen and nothing happens... I've no option left after searching on the net for answer so i rebooted.


My question is..
What happened? did it went to sleep mode or an error? and
Whats the default password for it? it did not ask me to create a username and password during installation.


Thanks in advance for the answer guys, appreciate it...



-Not Everything is Learned but to survive Learning is Everything

---

### Post by dstew on 2010-03-23
What method did you use to create the Ubuntu flashdrive? Provide a link to the site if you can. Maybe you did not leave enough space for the storage of new software. Open Office is pretty big.

---

### Post by naru2bon on 2010-03-26
Sorry for the late reply, I've used pendrivelinux.com's **Universal USB Installer **and set the persistance to 3gb and the installation went fine without any errors. 
 
I've been doing it a couple of times already (installing and reinstalling) and everytime i make changes, even minor changes like changing themes or updating nvidia's drivers it won't boot the next time i'm gonna use it and gives me different errors everytime. Now i'm having doubt if i'll be able to use it on my usb but of course its just a matter of trying and testing, which means i'm gonna need more patience. I'd like to carry around a working linux(ubuntu) with me on my usb and not rely on that ever-so-strict crappy windows os.
 
Any suggestions on making ubuntu work stable on a usb just like a normal OS that you can make changes to?
 
Thanks man for any ideas.

---

### Post by dstew on 2010-03-27
Sorry, I don't have any ideas on fixing the problem. I would probably try a different method of making the USB drive, like using [a Live CD and USB Creator]("http://http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/").

---

### Post by naru2bon on 2010-03-28
Thats allright man, thanks anyway. So far i have tried different persistence, i think the only thing i need to try now is use a different flashdrive, it might be with the flashdrive. For the meantime I'm trying out vmware and virtualbox in ubuntu.

---

### Post by C.S.Cameron on 2010-03-29
I don't think it is a good idea to update or upgrade a persistent flash drive, the kernel is part of a disk image that can't be changed.
If you want to update ot upgrade a pendrive install do a full install, (Just like you would install to an internal HD)using the install option from the live CD.

---

### Post by naru2bon on 2010-04-05
> **C.S.Cameron said:**
> I don't think it is a good idea to update or upgrade a persistent flash drive, the kernel is part of a disk image that can't be changed.
If you want to update ot upgrade a pendrive install do a full install, (Just like you would install to an internal HD)using the install option from the live CD.


So how do you permanently install ubuntu on a usb or an external hdd that connects thru usb? i would prefer using usb because i want to carry it around with me.

Any links or sites that you could recommend for a tutorial. Thanks =)

---

