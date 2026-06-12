---
title: "Black Screen"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by snipe6006 on 2008-06-07
I am installing Ubuntu 8 on a computer. I boot it up and then tall it to install. After the orange progress bar fills the screen goes black and a cursor show up then the monitor goes into sleep mode. I let it sit for an hour and nothing happened. What is wrong?
I am using the Desktop normal cd. I have even tried the alternate to no avail.
I appreciate your responses.

---

### Post by halln on 2008-06-07
It happened to me b4, I did a lot of how to.. nothing works, Only when i change my monitor solve my problem. I dont know if these helps. try to borrow a monitor to isolate your probs. or goggle some more info.

---

### Post by Unix_Slayer on 2008-06-07
There is something wrong with your monitor, or video config.

---

### Post by man not here on 2008-06-11
Greetings to all, 

I have exactly the same problem with trying to install Ubunutu or Xubuntu. The thing is I am using old Toshiba Laptop so I can't change monitors. 

Here are my specs:
Toshiba satelite S1800-400
Intel celeron 801 MHz
504 MB RAM
Trident Video Accelerator Cyberblade-Ai1

I wanted Xubuntu which "makes your old computer become alive again". I tried with the live CD but as the original post said after splash screen loading bar the screen just goes black, like on stand by. That's is the farthest it goes. I tried "blind log in" but nothing happens until I press ctrl+alt+del and restart it. Then I downloaded alternate install CD and after successfull installation when you take the CD out and boot the computer it happens exactly the same.

I read through many threads and tried different solutions (removing splash and quiet, reconfiguring x server etc.) but non of it worked. I tested on other computers and they work fine. 
I am familiar with computers but am reasonably new to Ubunutu/Xubuntu. 

So now I would really appreciate if anyone is able to help. I've been struggling with this for a week or so and now reached the point of giving up (which perhaps is what I should do if someone tells me that my configuration can't support Ubuntu).

Anyway thanks for reading this.

---

### Post by Unix_Slayer on 2008-06-11
> **man not here said:**
> Greetings to all, 

I have exactly the same problem with trying to install Ubunutu or Xubuntu. The thing is I am using old Toshiba Laptop so I can't change monitors. 

Here are my specs:
Toshiba satelite S1800-400
Intel celeron 801 MHz
504 MB RAM
Trident Video Accelerator Cyberblade-Ai1

I wanted Xubuntu which "makes your old computer become alive again". I tried with the live CD but as the original post said after splash screen loading bar the screen just goes black, like on stand by. That's is the farthest it goes. I tried "blind log in" but nothing happens until I press ctrl+alt+del and restart it. Then I downloaded alternate install CD and after successfull installation when you take the CD out and boot the computer it happens exactly the same.

I read through many threads and tried different solutions (removing splash and quiet, reconfiguring x server etc.) but non of it worked. I tested on other computers and they work fine. 
I am familiar with computers but am reasonably new to Ubunutu/Xubuntu. 

So now I would really appreciate if anyone is able to help. I've been struggling with this for a week or so and now reached the point of giving up (which perhaps is what I should do if someone tells me that my configuration can't support Ubuntu).

Anyway thanks for reading this.


Did you try running it in safemode?

---

### Post by man not here on 2008-06-12
Thanks for the reply. I tried in safe graphics mode plus in all other offered options from the boot up menu. The result was always the same - black screen after splash loading bar. 
I've been reading different threads and it seems quite a few people had similar problems, though they did find some solutions which didn't work for me when I tried them.

---

### Post by Unix_Slayer on 2008-06-13
> **man not here said:**
> Thanks for the reply. I tried in safe graphics mode plus in all other offered options from the boot up menu. The result was always the same - black screen after splash loading bar. 
I've been reading different threads and it seems quite a few people had similar problems, though they did find some solutions which didn't work for me when I tried them.

Maybe yoiur xorg.conf changed. If their is a backup of it in the /etc/X11 directory, you could try replacing it with the newest one.

---

### Post by man not here on 2008-06-14
Thanks again. I did that as well. I obtained the latest one but the result was the same. 
Anyway last night I switched to Debian instead of Ubuntu and installation all went very smoothly. I am writing this from my laptop now and everything works fine (though I do expect something to go wrong sooner or later). I didn't have to do any tweaking or so, just  put Debian installer CD and waited, that's all. Thanks for trying.

---

### Post by Tomatz on 2008-06-14
To fix this i will need your monitor/laptop screen specs.

---

### Post by heatpumpcontrol on 2008-06-14
Hey guys,

When you try the live CD, do you have a good display?

If you do then try this....

while on the live cd...

copy your xorg.conf file onto a jumpdrive or something.... another partition?

Or if you've already installed Ubuntu then mount the partition onto which Ubuntu is installed and cp (copy) the xorg file into the installed O/S. 

Don't forget to make a copy of your original xorg.conf file in the O/S.

If you need more help let me know.

use:

```
gksudo nautilus
```

to perform all the copying.

Miguel

---

### Post by man not here on 2008-06-16
> **Tomatz said:**
> To fix this i will need your monitor/laptop screen specs.

it seems that the problem was with the frame buffers. yesterday i was installing elive gem and the dialog box poped up saying that my monitor supports frame buffers but in case of enabling that option i might experience black screen on boot up. of course i disabled it so there were no problems with the install. it would be good if i knew this earlier when i was trying ubuntu/xubuntu, but it doesn't matter since now i will probably stay with elive.
thanks to all of you for trying though if someone knows how to disable frame buffers manually it would be good to post it for those people who are still struggling with the black screens. that might be a solution.

cheers.

---

### Post by Kevanx on 2008-06-18
@man not here

I started out on Ubuntu with the Toshiba Satellite 1800. From what I gather, the problem has to do with the trident cyberblade graphics card being 3D capable, but not supported within the linux kernel.

What worked for me was to Install using 6.04, and then upgrading to Feisty Fawn, but I was never able to upgrade to gutsy or hardy successfully, regardless of putting flags on the boot string, and modifying xorg.conf

That will almost definitely work if you *do* want to give ubuntu a try.

---

### Post by gmasters on 2008-10-20
I tried both 8.04 LTS and 8.10 beta with the same results. I then tried pressing Ft and appending "fb=false pci=noacpi noacpi nolapic" (without the qutoes) at the end of the comand line. As a result, I was able to get to the second half of the boot process where the bar grap just moves farther and farther to the right (rather than oscilating back and forth). Without the parameters, I never get to the second bar graph. However, I still get a blank screen with a flashing cursor and a hang.

---

### Post by loomsen on 2008-10-20
How about disabling that very informative bootscreen and looking at the messages then? :D

This lockups the ones a buddy of me had to fight on a Samsung with preinstalled Vista. After 3 days of googling and Bios option switching We finally managed to keep it running. Prior not even XP could be installed.

Turned out that, what else, Samsung and MS have a close cooperation, and that the Vista Recovery Partition is written to the ACPI tables in BIOS.

Hard piece of work to get that lock killed.

---

### Post by snipe6006 on 2008-10-20
Sorry for not replying, I forgot about this thread. Anyways I successfully installed Ubuntu, from the alternate live CD, by running it in low graphics mode. I did this to install Xubuntu as well. Now all I have to do is fix my resolution problem...

Thanks for all the reply's.

---

### Post by gmasters on 2008-10-22
> **snipe6006 said:**
> I am installing Ubuntu 8 on a computer. I boot it up and then tall it to install. After the orange progress bar fills the screen goes black and a cursor show up then the monitor goes into sleep mode. I let it sit for an hour and nothing happened. What is wrong?
I am using the Desktop normal cd. I have even tried the alternate to no avail.
I appreciate your responses.

This workaround worked on 8.10 and may also work on 8.04: Using the Live-CD desktop edition, I did a text install (it's the third item down from the boot menu). Ubuntu installed successfully, but came up with the black screen you also experienced.

I rebooted from Grub into reocvery mode and dropped to a root shell. I added the Option "NoDDC" as indicated in Michael Minn's xorg.conf file which I have reproduced below:

he workaround for the DDC bug is that you need to install an xorg.conf configuration file without DDC BEFORE installing the X Window system and the Ubuntu Desktop. The following is my /etc/X11/xorg.conf file. The key is the line in the "Device" that says Option "NoDDC". (reference)

	# xorg.conf (X.Org X Window System server configuration file)
	#
	# Custom file by Michael Minn

	Section "InputDevice"
		Identifier	"Generic Keyboard"
		Driver		"kbd"
		Option		"XkbRules"	"xorg"
		Option		"XkbModel"	"pc105"
		Option		"XkbLayout"	"us"
	EndSection

	Section "InputDevice"
		Identifier	"Configured Mouse"
		Driver		"mouse"
		Option		"CorePointer"
		Option		"Device"	"/dev/input/mice"
		Option		"Protoxol"	"ImPS/2"
	EndSection

	Section "Device"
	    Identifier    "Trident Microsystems CyberBlade/i1"
	    Driver        "trident"
	    BusID        "PCI:1:0:0"
	    Option	"NoDDC"
	EndSection

	Section "Monitor"
	    Identifier    "ToshLCD"
	    Option        "DPMS"
	    HorizSync      30-71
	    VertRefresh    50-100
	EndSection

	Section "Screen"
	    Identifier    "Default Screen"
	    Monitor       "ToshLCD"
	    Device        "Trident Microsystems CyberBlade/i1"
	    DefaultDepth    16
	    SubSection "Display"
        	Depth        16
	        Modes        "1024x768"
	    EndSubSection
	    SubSection "Display"
	        Depth        24
        	Modes        "1024x768" 
	    EndSubSection
	    SubSection "Display"
        	Depth        16
	        Modes        "800x600"
	    EndSubSection
	    SubSection "Display"
        	Depth        24
	        Modes        "800x600" 
	    EndSubSection
	EndSection

	Section "ServerLayout"
		Identifier	"Default Layout"
		Screen		"Default Screen"
		InputDevice	"Configured Mouse"
	EndSection


Unfortunately, it's a hoaky solution that works! The best solution is for the development teams of xorg and the ubuntu installer to set up the proper detection so you can try out the OS without insalling it and build some confidence in the user. Elegant simplicy is always a good thing!

---

### Post by daemoncat on 2008-10-23
My problem was unrelated except that I could not get a gui after a failed Edubuntu update via the interwebs. Every thing worked except for the screen. The best I could get was an "X" as a mouse cursor on a vertical barred green/black display. Adding the Display SubSections" worked! I'm using a very old nvidia TNT2 card, and the drivers specifically for older cards refuse to believe that it can't handle the super high resolutions that the newer monitor is capable of!

None of the nvidia problem threads included this simple fix. In the name of "streamlined and less confusing", they've essentially broken the xorg.conf file setup. "Configured Video Card" is a totally meaningless item, unless you can figure out where the devil to access its settings! GRRRR!! I think the default xorg.conf should have this type of thing commented out under the heading of "No Display Emergency Disaster Recovery".

Anyway, thanks for this solution.

---

### Post by K_REY_C on 2008-11-29
Hey... not sure if this is the place to post this question... but it seems closest to the issue I'm having:

Running ubuntu 8.04 desktop on a thinkpad t41 (been working fine for a good deal of time). 

Did some updates yesterday and now my screen goes black randomly:
1)Sometimes before login screen
2)Sometimes after login screen
3)Even when using different monitor with VGA out

Any thoughts on this? It's really frustrating as my laptop is unusable because I can't see anything.

Any help appreciated!

Thanks,

K_REY_C

---

