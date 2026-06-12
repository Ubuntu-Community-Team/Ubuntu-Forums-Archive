---
title: "Black Screen on Boot - Grub Related?"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by agxryt on 2013-02-21
Hey guys.

I've had this problem with all 12.10 *buntu distros...

It's an HP Pavilion G6, single boot, encrypted installation, lubuntu 12.10. 

Every other time I turn my laptop on, after I get the "HP" screen, I get a blank screen (like black, no backlight whatsoever). It does not resolve until I turn the computer off, turn it back on, and am brought to the grub menu. 

What's up with that?

Also, I recently disabled the grub menu (or so I thought), using the following method:

```
sudo leafpad /etc/default/grub 
```

> change "GRUB_TIMEOUT=10" to "GRUB_TIMEOUT=0"
> save
> sudo update-grub

Which worked for two reboots (did not fix the blank screen issue), and then the menu started popping up again.

Anyone have any insight?

---

### Post by JiuJitsu500 on 2013-02-21
Sounds like a weird driver issue perhaps?

Make sure the OS is fully updated and no additional drivers are necessary. From there we can solve this strange GRUB issue.

May be a bug you'd have to report, but let's start with the basics :popcorn:

The lines below that too can play a role, with acpi and such... try setting that to "1" and see if it persists. Odd problem man.

---

### Post by UltimateCat on 2013-02-21
Odd indeed-


Is it this HP?
[http://www.notebookreview.com/default.asp?newsID=6264&review=hp+pavilion+g6&p=3](http://www.notebookreview.com/default.asp?newsID=6264&review=hp+pavilion+g6&p=3)

---

### Post by UltimateCat on 2013-02-21
Came with Win's 7 so it's not the Win's 8 UEFI nonsense keeping the competitors out stuff-
You could try restoring the orginal graphics drivers mentioned in the last link I posted.

Wonder if a error log would provide an answer?
Sometimes I look up the error messages online and am able to find solutions that other Linux users have posted.

[http://h30434.www3.hp.com/t5/Notebook-Lockups-Freezes-Hangs/HP-Pavillion-G6-g6-1242sa-startup-Blank-screen-just-fan/td-p/1197579](http://h30434.www3.hp.com/t5/Notebook-Lockups-Freezes-Hangs/HP-Pavillion-G6-g6-1242sa-startup-Blank-screen-just-fan/td-p/1197579)

Troubleshooting HP Black or Blank Screen:
[http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=110&prodSeriesId=5046257&prodTypeId=3219](http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=110&prodSeriesId=5046257&prodTypeId=3219)
[http://www8.hp.com/us/en/support-drivers.html](http://www8.hp.com/us/en/support-drivers.html)

[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c01881110&lc=en&product=5118781](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c01881110&lc=en&product=5118781)

Hope this helps;)

---

### Post by agxryt on 2013-02-21
> **JiuJitsu500 said:**
> Sounds like a weird driver issue perhaps?

Make sure the OS is fully updated and no additional drivers are necessary. From there we can solve this strange GRUB issue.

May be a bug you'd have to report, but let's start with the basics :popcorn:

The lines below that too can play a role, with acpi and such... try setting that to "1" and see if it persists. Odd problem man.

When I was using 12.04, I would get some restricted video drivers... But I'm not sure how to get them now, because 12.10 doesn't seem to include the restricted drivers application, and I'm not quite sure if it's something I can just install and run :/

I'll give that a try, and edit it into this post.. I'm currently working with 1 pc, so it's a little difficult to move back and forth :P

> **UltimateCat said:**
> Odd indeed-


Is it this HP?
[http://www.notebookreview.com/default.asp?newsID=6264&review=hp+pavilion+g6&p=3](http://www.notebookreview.com/default.asp?newsID=6264&review=hp+pavilion+g6&p=3)

Not exactly that one. 700gb drive, 5 gigs of ram (don't ask me why)

According to the not-quite-functioning benchmark application, the processor is an AMD phenom II 960 quadcore

---

### Post by MAFoElffen on 2013-02-21
On backlight... 

Re-edit /etc/default grub
Goto the line:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
And edit to be... 
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

```
Save, exit, update-grub to pick up the changes...

Then edit /etc/rc.local
```

gksudo leafpad /etc/rc.local

```
Before the last line that says "exit 0", add a line and insert:
```

setpci -s 00:02.0 F4.B-0

```
Save and exit... Reboot.

If it still doesn't come up, change /etc/rc.local back (remove the added line). Edit /etc/default/grub and change "acpi_osi=Linux" to "acpi_backlight=vendor"... Save exit, upgdate grub and reboot.

If it doesn't come up again... edit /etc/default/grub and change "acpi_backlight=vendor" to "video.use_bios_initial_backlight=0"... Save exit, upgdate grub and reboot.

And if it still doesn't come up:
```

ls /sys/class/backlight/* > ~/backlight.txt

```
And post those results here.

---

### Post by MAFoElffen on 2013-02-22
But if not a backlight issue (read back through your posts) and instead trying to find "additional drivers" in >= v12.10... It has now moved System Settings > to a tab within the Software Sources app. Look for it as the right most tab.

---

### Post by agxryt on 2013-02-23
> **MAFoElffen said:**
> But if not a backlight issue (read back through your posts) and instead trying to find "additional drivers" in >= v12.10... It has now moved System Settings > to a tab within the Software Sources app. Look for it as the right most tab.

I may end up switching back to 12.04 after all...

It has taken me 20 minutes to get software sources to open. 

I'll try this before the backlight thing.

---

### Post by JafoFubar on 2013-02-23
> **MAFoElffen said:**
> But if not a backlight issue (read back through your posts) and instead trying to find "additional drivers" in >= v12.10... It has now moved System Settings > to a tab within the Software Sources app. Look for it as the right most tab.

Thank you. This worked for me....sort of. I changed to a proprietary driver the software sources app and now it reboots without the black screen and I can logon but, now I get no desktop. No unity bar on the right, no panel at the top, just the background and the mouse pointer. The pointer works but there's nothing to point at or click on! 


Update: I reinstalled, this time without encrypting the drive and it reboots fine without changing anything.

---

### Post by MAFoElffen on 2013-02-24
> **agxryt said:**
> I may end up switching back to 12.04 after all...

It has taken me 20 minutes to get software sources to open. 

I'll try this before the backlight thing.

If a backlight issue... ? Only if a laptop -and-...

If you hold a flashlight at an angle to a laptop screen and see the screen, but the backlight is not lighting up the screen... Then that applys. Another thing to do in that case is to use <Fn><right-arrow> or <Fn><Left-arrow> at that point to see if the brightness changes.  On some latops (one of mine does this) those controls are somehow reversed from what they should be- Meaning the function keys to make it lighter ends up actually being the opposite... and trying to make a dark screen darker...

---

### Post by MAFoElffen on 2013-02-24
> **JafoFubar said:**
> Thank you. This worked for me....sort of. I changed to a proprietary driver the software sources app and now it reboots without the black screen and I can logon but, now I get no desktop. No unity bar on the right, no panel at the top, just the background and the mouse pointer. The pointer works but there's nothing to point at or click on! 


Update: I reinstalled, this time without encrypting the drive and it reboots fine without changing anything.
Still not a good match yet then... 

If you could post the results of this-
```

lspci -vnn | grep -i VGA

```
That would tell me the video hardware you have and I could recommend a good match in drivers...

EDIT--Saw your edited update. AS the OP, please mark this thread as "Solved."

---

