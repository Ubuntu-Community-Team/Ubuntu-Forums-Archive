---
title: "Linux installed &quot;successfully&quot; then black screen"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by Glenbejamin on 2010-10-16
So i just bought a cheep notebook for school. Not being a fan of windows I decided try and download Ubuntu 10.10 for the laptops. I downloaded the content on a flash drive since it has no disk drive and it installed. It seemed to be running fine, then it said to finish I need to restart. So i did, but all that comes up is the Acer start up (with option to hit F2 for options) and then goes directly to a black screen with a flashing cursor. It makes no sounds other then a beep when I hit too many button. It gives me no other options and I have no clue whats going on.

---

### Post by mörgæs on 2010-10-17
Hi, welcome to the forum.

How does the machine behave, if you install 10.04?

---

### Post by Glenbejamin on 2010-10-17
I'll try running it. The thing is I was so eager to get rid of windows I chose the Erase Hard drive option. Would I just load this version to the USB drive and tell the laptop to run the USB first and hope for the best?

---

### Post by mörgæs on 2010-10-17
Yes, that is the way to go. You can change the boot order in BIOS, if USB is not first already.

I am not saying that it is impossible to get 10.10 to work; it will just be good to have 10.04 running for comparison.

---

### Post by Glenbejamin on 2010-10-17
So i tried that and got the same result. I really hope my laptop is still usable. I'm just hoping it can run any OS at this point.

---

### Post by mörgæs on 2010-10-17
I can almost promise you that the machine is all right. Most likely it just needs some boot parameters.

---

### Post by Glenbejamin on 2010-10-17
I think the problem is the lack of a disk drive on the laptop. My desktop is a Mac, so how exactly would i properly get the flash drive ready to boot a version of Linux. BTW witch version would you recommend? It's not a powerful laptop, all I need is some a office suite and web browsing and I'd prefer something really stable.

---

### Post by mörgæs on 2010-10-18
Let's hear some specifications for the machine.

Here are some boot parameters which might help to boot:
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

### Post by Glenbejamin on 2010-10-18
It's an Acer Aspire one. It has an Intel Atom processor N450, 1 GB memory, 160 GB Hard drive. Any thing else you want to know? I know there are probably fridges out there with more processing power then this, but it is small enough to be a chocking hazard lol.

I haven't even got to that install menu yet. The weird thing is, Ubuntu was running fine during the installation proses. But then when I restarted it, and every time i start it up I just get a solid black screen with a flashing cursor in the top left corner.

---

### Post by mrnelson1986 on 2010-10-18
Can you boot from the live cd still? I have a problem with my laptop (sony vaio) that I am able to fix by adding the text "nomodeset" to the boot options.  The problem is that ubuntu doesn't recognize my video card (nvidia gt 330M) by default due to the proprietary sony drivers being required, so you have to fuss around with it a bit.  It sounds like the same problem I used to have (black screen).

It's possible it is some other problem, but you never know...only other thing I can think of off the top of my head is that during installation, GRUB isn't being installed correctly.

---

### Post by Glenbejamin on 2010-10-19
That seems to be my problem, but the thing is the laptop has no disk drive and that is making this very difficult.

---

### Post by mörgæs on 2010-10-19
> **Glenbejamin said:**
> It's an Acer Aspire one. It has an Intel Atom processor N450, 1 GB memory, 160 GB Hard drive. Any thing else you want to know? I know there are probably fridges out there with more processing power then this, but it is small enough to be a chocking hazard lol.

I haven't even got to that install menu yet. The weird thing is, Ubuntu was running fine during the installation proses. But then when I restarted it, and every time i start it up I just get a solid black screen with a flashing cursor in the top left corner.

The specifications look fine. 

Which boot parameters have you tried? Nomodeset?

---

### Post by mrnelson1986 on 2010-10-19
> **Glenbejamin said:**
> That seems to be my problem, but the thing is the laptop has no disk drive and that is making this very difficult.

might not be terribly useful, but I make USB stick install "discs" instead of the CD's....I don't have a lot of CD's and it's a pain to burn them when I can just write to a USB, you could try that?

---

### Post by mörgæs on 2010-10-20
USB's work fine, but it is important to create them with the right applications. The version of Unetbootin which comes in 10.04 does not work, but downloading the latest Unetbootin does.

---

### Post by mjh_ca on 2010-10-20
It's possible that the install just failed for some reason and it needs to be run again.  

You could just buy or borrow an external USB CD drive, burn the ISO to a CD and install from there.  Pretty sure the Netbook will boot from a USB CD drive and then you can save yourself the effort of trying to figure out why it won't boot from the USB stick.  Creating a bootable USB stick is usually more difficult than burning a CD, especially if you aren't familiar with the process.

If you can't buy/borrow a USB CD drive and really want to do the USB method, here is a way that will definitely work.  Burn an Ubuntu 10.10 CD using your mac, then boot your mac with that LiveCD (click "Try Ubuntu" when it boots).  Once Ubuntu has booted, go to System > Administration > Startup Disk Creator.  From there you can create a bootable USB from the Ubuntu 10.10 ISO for your netbook.

---

