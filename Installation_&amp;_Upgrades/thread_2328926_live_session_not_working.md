---
title: "live session not working"
date: 2016-06-25
forum: Installation &amp; Upgrades
---

### Post by donmatas on 2016-06-25
Hi,

I had windows XP installed in a partition that I have formated by mistake. Now I try to run a bootable usb but it is not working. It just goes back to the grub without loading the live session of the usb stick.

Does anyone know what to do?

---

### Post by RobGoss on 2016-06-25
Hello and welcome to the forum,  can you tell us how you created this USB and what software did you use to create?

What are the specs for this machine I'm guessing if it is running Windows XP it's not have UEFI and you may need to change your configurations 

Did you configure your BIOS to boot from the USB stick some older machine with not recognize a USB drive and may need to booted from a **DVD** or **CD** drive

---

### Post by donmatas on 2016-06-27
> **RobGoss said:**
> Hello and welcome to the forum,  can you tell us how you created this USB and what software did you use to create?

What are the specs for this machine I'm guessing if it is running Windows XP it's not have UEFI and you may need to change your configurations 

Did you configure your BIOS to boot from the USB stick some older machine with not recognize a USB drive and may need to booted from a **DVD** or **CD** drive

Hi Robgoss,

I am using a Dell Inspriron 1545. I have no idea about UEFI, but I have booted my computer with a USB stick many many times without problems, so it can recognize usb drive for booting. 
This time I used unetbootin to create the USB live session.

---

### Post by RobGoss on 2016-06-27
> **donmatas said:**
> Hi Robgoss,

I am using a Dell Inspriron 1545. I have no idea about UEFI, but I have booted my computer with a USB stick many many times without problems, so it can recognize usb drive for booting. 
This time I used unetbootin to create the USB live session.

I see a lot or people having trouble with unetbootin creating a live USB drive

Try using **Pendrive **to create your **USB** live installer [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by donmatas on 2016-06-28
> **RobGoss said:**
> I see a lot or people having trouble with unetbootin creating a live USB drive

Try using **Pendrive **to create your **USB** live installer [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Thanks RobGoss. I am used to use usb-creator (which is the utility preloaded in ubuntu). Do you think that is a good idea to install it in Xubuntu?

---

### Post by RobGoss on 2016-06-28
I miss understood you I was under the impression you were using Windows, Yes USB creator is just fine

---

### Post by donmatas on 2016-06-28
> **RobGoss said:**
> I miss understood you I was under the impression you were using Windows, Yes USB creator is just fine

Perfect! 

Just to clarify my problem. I had two partitions: one with XP, and the other one with Xubuntu. I erased by mistake the former, and I wanted to boot the laptop from the usb, in order to delete the partition and add it to my /home.

best!
M

---

### Post by RobGoss on 2016-06-28
Which one did you erased by mistake XP or Xbuntu? 

And is there a operating system currently on this machine

---

### Post by donmatas on 2016-06-28
> **RobGoss said:**
> Which one did you erased by mistake XP or Xbuntu? 

And is there a operating system currently on this machine

Fortunately, I erased the XP partition. The machine is working fine with Ubuntu. The only issue is that I cannot boot from the USB. I will check if the problem is the stick itself, by mounting the image with usb-creator instead of unetbootin. I will post the results here.

---

### Post by RobGoss on 2016-06-28
You will probably have to go into your BIOS and change the boot order to boot from the USB device some machines bios can be accessed using F12 then you can change how your machine will boot

Some cases require moving up the boot order so that you can choose what device need to be first in line

If you are unable to access your BIOS try reading your machines manual of doing a Google search for more info on it

---

### Post by donmatas on 2016-06-28
> **RobGoss said:**
> You will probably have to go into your BIOS and change the boot order to boot from the USB device some machines bios can be accessed using F12 then you can change how your machine will boot

Some cases require moving up the boot order so that you can choose what device need to be first in line

If you are unable to access your BIOS try reading your machines manual of doing a Google search for more info on it

Thanks RobGoss, but is not a problem of Bios' boot order. I am very familiarized with it, and I am sure that is properly configured. Actually, I have been trying different distros in the last month without any problem. The issue appears after formating the XP partition, but it could be a problem of the stick. I will try mounting the iso with usb-creator, and I will report the results.

---

### Post by donmatas on 2016-06-29
> **donmatas said:**
> Thanks RobGoss, but is not a problem of Bios' boot order. I am very familiarized with it, and I am sure that is properly configured. Actually, I have been trying different distros in the last month without any problem. The issue appears after formating the XP partition, but it could be a problem of the stick. I will try mounting the iso with usb-creator, and I will report the results.

It was a problem with the stick. I made a new one with usb-creator (instead of unetbootin), and now it works

Thank you for your help!

---

### Post by QDR06VV9 on 2016-06-29
Good Work:)
Now if you would mark this as solved to helps other visitors looking for similar.

---

