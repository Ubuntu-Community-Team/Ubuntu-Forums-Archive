---
title: "&quot;Minimal BASH-like&quot; problem"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by Macgyver150 on 2011-06-01
Hello,
I have a problem with booting my Ubuntu System.
I have installed the new version of Ubuntu(11.04) next to Windows XP on my PC. When I restarted my PC I have selected "Ubuntu" from the boot menu. When I did that following massage arrived at my screen:

"[CENTER]GNU GRUB  version 1.99"rc1-13ubuntu3[/CENTER]

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command complections. Anywhere else TAB lists possible device or file complections

grub> _"

Can you please help me to start Ubuntu, best in German? 
Tanks,
Matthias

---

### Post by Hedgehog1 on 2011-06-02
Hello!


We need to get a look at your install to get an idea what is going on.

Please boot off the Ubuntu LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge (der Igel?)***

:KS

---

### Post by Macgyver150 on 2011-06-02
with which program I should do that: ????:(:(

"Open a terminal (Applications -> Accessories -> Terminal in Gnome) and type :
  sudo bash [path/to/the/download_folder]/boot_info_script.sh
For example if you downloaded the file to the desktop, use:
  sudo bash ~/Desktop/boot_info_script.sh
If your operation system does not use sudo, use:
  su 
  bash ~/Desktop/boot_info_script.sh"

I dont have 'Terminal in Gnome'

---

### Post by MeghalShah on 2011-06-02
I am facing similar problem, i have been using it until last night  .  Today powering it up, its showing up the same error. I am running Ubuntu on Vista.

---

### Post by Hedgehog1 on 2011-06-02
> **Macgyver150 said:**
> with which program I should do that: ????:(:(

"Open a terminal (Applications -> Accessories -> Terminal in Gnome) and type :
  sudo bash [path/to/the/download_folder]/boot_info_script.sh
For example if you downloaded the file to the desktop, use:
  sudo bash ~/Desktop/boot_info_script.sh
If your operation system does not use sudo, use:
  su 
  bash ~/Desktop/boot_info_script.sh"

I dont have 'Terminal in Gnome'

You will need to use an Ubuntu CD, and boot from that.  The desktop version of the Ubuntu CD allows you to boot from computer from the CD, then run Ubuntu from the CD (called the 'TRY' option).  From that CD based version of Ubuntu, you can run the boot info script & post the script output in this thread.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-06-02
> **MeghalShah said:**
> I am facing similar problem, i have been using it until last night  .  Today powering it up, its showing up the same error. I am running Ubuntu on Vista.

MeghalShah,

**Please create a separate thread with your issue** (we don't want to high jack this thread, it belongs to Macgyver150).

When you create your new thread, please include the output of the boot info script using the instructions I gave Macgyver150 in post #2, it will spredd up your getting help.

***The Hedge***

:KS

---

### Post by Macgyver150 on 2011-06-02
schould I uninstall my broken ubuntu before I start booting from the CD?

---

### Post by Hedgehog1 on 2011-06-02
> **Macgyver150 said:**
> schould I uninstall my broken ubuntu before I start booting from the CD?

The reason for running the script requested here:

> **Hedgehog1 said:**
> Hello!

We need to get a look at your install to get an idea what is going on.

Please boot off the Ubuntu LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge (der Igel?)***

:KS

Is to give us information about your Ubuntu install in it's current state, and from the script output we can (usually) give you the steps to fix the install.

So please do not attempt to remove the Ubuntu install, instead boot from the CD and run little Ubuntu from the CD using the 'TRY' option), and then follow the step to create the RESULTS.TXT file, then post the contents of the RESULTS.TXT file in this thread.

Thanks!

***The Hedge***

:KS

[IMG]http://www.ubuntu.com/sites/www.ubuntu.com/files/active/natty/01-welcome.jpg[/IMG]

[IMG]http://www.ubuntu.com/sites/www.ubuntu.com/files/active/natty/02-live-cd-desktop.jpg[/IMG]

**[WHERE IS THE TERMINAL?]("http://www.psychocats.net/ubuntu/terminal")**

---

