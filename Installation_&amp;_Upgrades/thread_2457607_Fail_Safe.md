---
title: "Fail Safe"
date: 2021-02-05
forum: Installation &amp; Upgrades
---

### Post by max8425752574 on 2021-02-05
Hi all,
I'm experienced some problems to start Ubuntu and ask for to make it fail safe?

It happened that some years ago my PC smelled like burning electronics but nothing worse happened.
About 18 months ago the PC had an head crash but I could reinstall Windows XP and backup my data. I had some problems with my USB harddrive but it worked. I also could start Ubuntu from DVD and USB stick. That all with the USB 3 ports from my PC! But sometimes Ubuntu was trapped and didn't start. I'm sorry I can't say why.

Now it looks that the USB ports 3 are dead completely. USB 2 works almost fine (with Windows). (The reason why I haven't experienced problems is that my keyboard and mouse works with the USB 2 ports. I only use USB 3 for backups or starting Ubuntu from USB stick because my tower has USB 3 at the front). (And again USB 3 worked sometimes and sometimes not)

But now with USB 3 complete dead it looks to me that Ubuntu will not boot again. Windows hasn't a problem.

Is it true that Ubuntu try to access the USB 3 ports and then is trapped in a loop?

Thanks

---

### Post by CelticWarrior on 2021-02-05
You can boot the installation media in the USB2 ports if the USB3 ports don't work. The only difference is speed.

---

### Post by max8425752574 on 2021-02-05
I haven't try to boot from USB 2 but I created a DVD first and now I can't boot from DVD.

After the hard drive crash I created a Ubuntu DVD and I could boot almost every try. Okay I didn't know what was wrong maybe I had to do a hard reset to boot.
Then I created the USB stick and sometimes it worked and then not

---

### Post by CelticWarrior on 2021-02-05
Maybe you should check your hardware?

---

### Post by TheFu on 2021-02-05
The BIOS controls the boot device order. Some are setup to boot from internal disks first, so external are ignored. Some flash storage doesn't work with some usb ports. I've never found a reliable way to know which will or won't work.

---

### Post by max8425752574 on 2021-02-05
As mentioned above I could boot from DVD and USB stick. But not every time. But I could boot. I could use Ubuntu to do a backup from my Harddisk.

Some months later I'm now unable to boot Ubuntu and I haven't changed anything in the BIOS. In those months I used a demo from Windows 7 and now I'm using Windows vista.

It's that Ubuntu forces a reset

I thought I've checked my hardware. A USB stick with a light showed me that the port has power.
But neither Windows or the BIOS shows me the stick any longer

---

### Post by CelticWarrior on 2021-02-05
> [COLOR=#000000]Some months later I'm now unable to boot Ubuntu and I haven't changed anything in the BIOS.[/COLOR]
And don't you think you should check the boot order? Have you even tried the one-time boot menu (if available)?

> [COLOR=#000000]In those months I used a demo from Windows 7 and now I'm using Windows vista.[/COLOR]
Both Windows versions are dangerous because they're out of support for quite some time, especially Vista. The ONLY Windows version that have support currently are Windows 8.x and Windows 10.
If your computer can run modern Ubuntu it can run Windows 10 as well. This may come as a surprise but it's exactly how thing are. Of course, within the Ubuntu "family" one can choose lighter flavors that work better with older and/or underpowered computers. But if you already tested vanilla Ubuntu (Gnome DE) and it works acceptably then you should be fine as well with Windows 10. Under NO circumstance use an obsolete OS, Windows or Linux based, connected to the internet.

Please post your hardware specifications for better suggestions.

---

### Post by TheFu on 2021-02-05
How old is the motherboard battery?  It really sounds like the BIOS is flaky and perhaps some other hw problem that MS-Windows is overlooking.

---

### Post by max8425752574 on 2021-02-05
Indeed. I've experienced a empty battery some time before. But then I got a BIOS message &#129316;

How can I check what happened to the USB 3 ports?
Because I'm sure that they died and that's the reason why Ubuntu crashes by booting.

And I think the next user will tell me about my graphics driver ...
I thought I should the Ubuntu developer about a problem but now I understand I've failed ....

Sorry Ubuntu community &#128532;

It looks to me that Linux never will do to the common user.

Bye bye

---

### Post by TheFu on 2021-02-05
If any usb port isn't on-line, the OS won't see it and nothing will happen.
**lsusb** can show usb ports and connected devices.

Booting off usb is different from seeing or accessing usb devices.

A short somewhere on the motherboard can cause all sorts of issues. I've seen a cracked motherboard seem to work perfectly, except some network packets would become corrupted., sometimes. This was at a software job and we qickly figured out which of 20 desktops had some issue, since only files being worked on by one developer got corrupted during check-in. Everyone else received those files corrupted when they "pulled" the updates. 
I fear you don't have another computer to troubleshoot?

**inxi -Fz** output would be of some help, if it can be provided. Also, the system log files most likely announce hardware problems.  [https://ubuntu.com/tutorials/viewing-and-monitoring-log-files#1-overview](https://ubuntu.com/tutorials/viewing-and-monitoring-log-files#1-overview) and [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by max8425752574 on 2021-02-06
Thx for the first seriously answer :)

But all I can say is that Windows and the BIOS ignore that the PC lost USB 3 probably because of an hardware failure.

But Ubuntu crashes and didn't start.

All I ask is to make it 'fail safe"

> **TheFu said:**
> 

A short somewhere on the motherboard can cause all sorts of issues. I've seen a cracked motherboard seem to work perfectly, except some network packets would become corrupted., sometimes. 

I think this happened to my USB ports. I could use them but not every time. I thought it was a problem with the cable.

Yes, I have another PC

---

### Post by TheFu on 2021-02-06
> **max8425752574 said:**
> It looks to me that Linux never will do to the common user.

Bye bye

Perhaps you should run Windows on this hardware instead? 
I'm guessing the possible data loss due to broken hardware doesn't matter?

No OS can deal with sufficiently broken hardware, especially when it is semi-broke, but sometimes appears (to a human) to work. 

I've learned that if my car stops when I'm driving down the road without any warning, then it is almost always due to a clogged fuel filter.  I don't blame the computers in the car as I'm coasting to a stop.  It isn't their fault that no fuel is getting to the fuel injectors (if that really is the issue).  Perhaps I should stop driving a car? After all, if it doesn't work when there is fuel in the tank, what good is it?  My horse never just stopped like that. Cars are inferior, clearly.

Do you see the point?

---

### Post by max8425752574 on 2021-02-06
My gallbladder has been removed and I can live with it as long as I spread my meals throughout the day.

Do you see the point?

As long as my PC work I'll keep it and now that I know the problem I can avoid it.

Imagine someone used a "USB Kill" stick on your computer and only half of the USB ports die why not use this computer

I'm using computers for about 30 years and every time I tried Linux I failed.

[https://www.bbc.com/news/technology-52891650](https://www.bbc.com/news/technology-52891650) &#128072; picture crashes Android

It's obvious that I'm wrong here.

Sorry that I haven't the hardware you expect

---

