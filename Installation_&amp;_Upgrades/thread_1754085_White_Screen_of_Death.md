---
title: "White Screen of Death"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by GNUoob on 2011-05-09
Hi all,

Thanks for taking the time to read/view/respond in whatever order you managed to get through.

Short of it is I installed ubuntu but 10.10? but cant get into the gui as it white screens at some point. 

I am sure it is a graphics issue but being an ID-10-T am unable to figure out the correct commands to kill the GUI and force it to reconfigure for this machines graphics stuff. *(long story time)

*= laptop has a dead cdrom so i pulled the hd out and installed on a tower using an adapter and plugged it back into the laptop.

Reason for 10.10 is i have two small kids and little time. my pet projects right now are limited to their sleeping schedules and honey do lists. yes it was 6 months ago i started this.

Edit- video linkage
[https://docs.google.com/leaf?id=0BwDjiw5_Hs-gZmZjZjRiNDYtMWI0ZS00NDM5LThmZjAtYzNkMWJlMmE2ZWIz&hl=en](https://docs.google.com/leaf?id=0BwDjiw5_Hs-gZmZjZjRiNDYtMWI0ZS00NDM5LThmZjAtYzNkMWJlMmE2ZWIz&hl=en)

---

### Post by Najubhai on 2011-05-11
I assume you have ATi Graphics card,if so then just go to the Grub2 menu scroll down to the line linux \boot and press end
Next press space and write radeon.modeset=0 (for nVidia write nomodeset)
and then press ctrl+x.Hopefully it will boot into the desktop.

NOTE: this is only a temporary fix so when successfully booted just update your drivers and you'll be good to go. :)

---

### Post by GNUoob on 2011-05-12
The system statistics are...

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=155145&rpn=PS500U&modelFilter=5005-S507&selCategory=2756709&selFamily=1073768663](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=155145&rpn=PS500U&modelFilter=5005-S507&selCategory=2756709&selFamily=1073768663)

From link...
NVIDIA GeForce4 440 Go, 32MB DDR video memory

---

### Post by GNUoob on 2011-05-13
> **Najubhai said:**
> I assume you have ATi Graphics card,if so then just go to the Grub2 menu scroll down to the line linux \boot and press end
Next press space and write radeon.modeset=0 (for nVidia write nomodeset)
and then press ctrl+x.Hopefully it will boot into the desktop.

NOTE: this is only a temporary fix so when successfully booted just update your drivers and you'll be good to go. :)

1) No ATI graphics

2) The GUI never loads as seen in the video I attached so I am unable to do any editing.

Thanks anyway.

---

### Post by lnebrown on 2011-05-17
Hello!

I'm having the same problem, I think, but with my upgrade to 11.04.  It boots to a white screen with some odd gibberish text.  It appears that this gibberish text is a terminal, as i believe i can "blindly" give my username, password and issue some commands like "sudo reboot".

Here is a link to my motherboard/video part:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131483R](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131483R)

Onboard video is NVIDIA GeForce4 MX, and it gave me some trouble with my previous upgrade to 10.10, but nothing like this.

Help!  Thanks!

---

### Post by GNUoob on 2011-05-17
I was/have been able to install 8.04 but attempting to upgrade to 10+ series produces the white screen. I have since dumped the upgrade and re-installed it back to 8.04.

So far I have not been able to find any answers while googling

---

### Post by GNUoob on 2011-06-04
Just checking back to see if anyone else might have had an idea/answer

:/

---

### Post by GNUoob on 2011-06-21
checking back

---

### Post by GNUoob on 2011-08-03
No additional answers :(

---

### Post by gordintoronto on 2011-08-03
> **GNUoob said:**
> 1) No ATI graphics

2) The GUI never loads as seen in the video I attached so I am unable to do any editing.

Thanks anyway.

The suggestion was to make the changes before the GUI loads, at the GRUB stage. That's the menu which asks what you want to run.

---

### Post by GNUoob on 2011-09-07
> **gordintoronto said:**
> The suggestion was to make the changes before the GUI loads, at the GRUB stage. That's the menu which asks what you want to run.

Hi, I recorded a video and attached it. I never have the chance to change that as seen in the video.

---

### Post by GNUoob on 2012-05-02
I will try to install 12.04 and see if that release fixes the issue.

---

