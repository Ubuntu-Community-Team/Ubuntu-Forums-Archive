---
title: "Howto install nouveau?"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sgage on 2010-03-04
What is the current state of the art for installing the latest nouveau?

---

### Post by philinux on 2010-03-04
System>admin>hardware drivers.

Select nVidia riva/tnt/geforce

---

### Post by sgage on 2010-03-04
I see no such option in my Hardware Drivers - just the two nvidia drivers (current and 173).

Is there something I need to do to have that option presented? Some ppa or some such?

---

### Post by philinux on 2010-03-04
> **sgage said:**
> I see no such option in my Hardware Drivers - just the two nvidia drivers (current and 173).

Is there something I need to do to have that option presented? Some ppa or some such?

Are you testing lucid or running Karmic?

---

### Post by sgage on 2010-03-04
I'm testing lucid.

---

### Post by philinux on 2010-03-04
Whats your graphics card? I'm running a 8600gt and a default lucid install.

Is your system fully up to date?

---

### Post by sgage on 2010-03-04
My graphics card is an 8500GT.

Totally up to date as of half an hour ago - 12:30 EST.

Do I have to uninstall the nvidia drivers to make the new option appear?

---

### Post by haydoni on 2010-03-04
I don't see it anymore either!
(It was there yesterday)

...but to be fair my system may not be fully upto date... updating....

---

### Post by philinux on 2010-03-04
> **sgage said:**
> My graphics card is an 8500GT.

Totally up to date as of half an hour ago - 12:30 EST.

Do I have to uninstall the nvidia drivers to make the new option appear?

Have a peek in synaptic. Search for nouveau.

This is whats installed here.

---

### Post by haydoni on 2010-03-04
The options should appear regardless of what is currently "active".

After updating and a restart: the Nouveau driver should appear in the hardware drivers (it had disappeared for a day or so! - at least it did for me).

---

### Post by philinux on 2010-03-04
+1 ^^^, yes after update/upgrade you will need to reboot.

---

### Post by sgage on 2010-03-04
Well, after uninstalling the nvidia drivers, rebooting, and installing the indicated files in Synaptic, a reboot brought me up into the nouveau drivers.

And now the option shows in Hardware Drivers. Better late than never, I always say ;)

Thanks for that screenshot from Synaptic!

---

### Post by The Pixel Developer on 2010-04-11
Hi,

I'm having a similar issue.

I can't find nouveau in the hardware panel: 

[IMG]http://www.ubuntu-pics.de/bild/51627/screenshot_002_3l2h5C.jpg[/IMG]

and here is the search in synaptic:

[IMG]http://www.ubuntu-pics.de/bild/51628/screenshot_003_kqDTDN.jpg[/IMG]

I noticed in philinux's screenshot there's linux-backports ... I can't seem to find those packages.

---

### Post by cascade9 on 2010-04-11
> **philinux said:**
> Whats your graphics card? I'm running a 8600gt and a default lucid install.

Is your system fully up to date?

Sort of off-topic, but why is it that you only have the 173 drivers avaible? That card should eb using 185/190/195.

---

### Post by Uncle Spellbinder on 2010-04-11
Same here. Nouveau is installed according to Synaptic, yet it does not appear in Hardware Drivers list. I'm fully updated Beta 2 running nVidia 9800GT

---

### Post by Uncle Spellbinder on 2010-04-11
> **cascade9 said:**
> Sort of off-topic, but why is it that you only have the 173 drivers avaible? That card should eb using 185/190/195.

Not me...

[IMG]http://i41.tinypic.com/mah4ir.jpg[/IMG]

---

### Post by Owen.C93 on 2010-04-11
I'm using the driver and it doesn't even show up in hardware drivers. It's done this for ages though.

I see what the post above shows.

---

### Post by bash on 2010-04-11
> **Uncle Spellbinder said:**
> Not me...

[IMG]http://i41.tinypic.com/mah4ir.jpg[/IMG]

Well the *(version current)* in Lucid is the 195.36.15 driver. Pretty up to date I would say.

---

### Post by Uncle Spellbinder on 2010-04-11
> **bash said:**
> Well the *(version current)* in Lucid is the 195.36.15 driver. Pretty up to date I would say.
Indeed. I was pointing out that 173 is present. Thought that was rather strange. Still, no clue why Nouveau is not on the list as it is installed according to Synaptic.

---

### Post by mc4man on 2010-04-11
Seeing as that nouveau is installed and used by default then the question (if there is one), is how to return to nouveau if one is using a restricted driver.

I'd assume there was/is the intention you could do so thru "Hardware Drivers", though atm that is not possible.

You can however use the more direct method of 'update-alternatives' to switch back and forth.


The number of available restricted drivers shown in Hardware Drivers is based on the model of your display adapter, though in most cases 'version current' is the best choice (nvidia 7XXX and newer here.

---

### Post by The Pixel Developer on 2010-04-11
> **Owen.C93 said:**
> I'm using the driver and it doesn't even show up in hardware drivers. It's done this for ages though.

I see what the post above shows.

How do you determine what driver you're using and how do you change to it when it's not in the hardware panel?

---

### Post by mc4man on 2010-04-11
> How do you determine what driver you're using

If you are using a restricted driver (nvidia) then ck. in System -> Admin. -> Nvidia X server settings, it will tell you.
Or run in terminal
```
nvidia-settings -q NvidiaDriverVersion
```

otherwise install this
```
sudo apt-get install mesa-utils
```
then run 
glxinfo
If the vendor string (4th line) is SGI then you're using nouveau, if it's NVIDIA ... 

> how do you change to it

change to what?

---

### Post by The Pixel Developer on 2010-04-11
> **mc4man said:**
> change to what?

Nouveau. I'm running the Nvidia driver atm.

---

### Post by Owen.C93 on 2010-04-11
> **The Pixel Developer said:**
> Nouveau. I'm running the Nvidia driver atm.
Install nouveau via terminal, then the nvidia drivers will not be in use but you will be able to get the benefits of nouveau. Like plymouth.

---

### Post by mc4man on 2010-04-11
To use update-alternatives to switch back  to nouveau follow the instr.'s here ( under 'or'

[http://ubuntuforums.org/showthread.php?t=1423210](http://ubuntuforums.org/showthread.php?t=1423210)

Edit; when jockey is fixed then method 1 in link will also work

---

### Post by The Pixel Developer on 2010-04-11
> **mc4man said:**
> To use update-alternatives to switch back  to nouveau follow the instr.'s here ( under 'or'

[http://ubuntuforums.org/showthread.php?t=1423210](http://ubuntuforums.org/showthread.php?t=1423210)

Edit; when jockey is fixed then method 1 in link will also work

Perfect, thank you.

---

### Post by mc4man on 2010-04-11
Just in case....

Now while I haven't bothered to find the 'exact' min. to go back to nvidia drivers with alternatives, this has worked fine (I use nvidia-current

sudo update-alternatives --config gl_conf

pick the nvidia driver ( here I use the 'auto mode' choice

sudo ldconfig
sudo update-initramfs -u
sudo nvidia-xconfig

restart

---

### Post by nanog on 2010-04-11
> What is the current state of the art for installing the latest nouveau?


[PHP]sudo add-apt-repository ppa:xorg-edgers/ppa[/PHP]

reboot

ctr-alt-F1

[PHP]compiz --replace &[/PHP]

ctrl-alt-F7

(jockey does not work well with gallium 3D driver)

---

### Post by FrancoNero on 2010-04-13
i have nouveau installed. but it's not an option. how do i get nouveau? it's like it's gone

---

### Post by mc4man on 2010-04-13
> i have nouveau installed. but it's not an option
Possibly it's not an option because it's the default - it's what you're using unless you replace it.

If so, then remove what you replaced it with, either in Hardware Drivers or directly with update-alternatives if using the ubuntu restricted drivers.

---

### Post by FrancoNero on 2010-04-13
there's not way to disable the nvidia driver really... don't wanna remove it just deactivate it or something...

---

### Post by mc4man on 2010-04-13
> there's not way to disable the nvidia driver really... don't wanna remove it just deactivate it or something...

Well it's all there in previous page, link in post 25 shows how to switch from nvidia to nouveau, # 27 to switch back to nvidia.
(using the update-alternatives method, only for the ubuntu supplied nvidia drivers

Quoting the relevant part from link - to return to nouveau from 'restricted nvidia driver' using update-alternatives

> OR

2) Open the terminal and type the following commands:

```
sudo update-alternatives --config gl_conf
```

(and select the alternative provided by mesa)

```
sudo ldconfig
sudo update-initramfs -u
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```

and restart your computer.

---

### Post by coffeecat on 2010-04-14
> **mc4man said:**
> Well it's all there in previous page, link in post 25 shows how to switch from nvidia to nouveau,

If my experience is anything to go by, there is one more step you need take to switch from nvidia to default nouveau.

After:

> Open the terminal and type the following commands:
     ```
sudo update-alternatives --config gl_conf
```(and select the alternative provided by mesa)```
sudo ldconfig
sudo update-initramfs -u
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```and restart your computer.... I was dumped into a low resolution desktop. I guess using the vesa driver. Fortunately, a vague memory of a post from a couple of weeks back prompted me to have a rummage in /etc/modprobe.d/. After commenting out the two lines in /etc/modprobe.d/blacklist-kernel-nouveau.conf so that it reads:

```
# blacklist nouveau
# blacklist vga16fb
```... I was able to boot into a proper desktop once more. Nice to see a decent Plymouth again - if only fleetingly. :wink:

Now I'm going to have a go at installing the xorg-edgers ppa nouveau to see if I can get compiz back with this GeForce 8400GS.

**Edit: **:( No compiz with xorg-edgers nouveau here. I'll try again with a newer version in due course.

---

### Post by mc4man on 2010-04-14
> If my experience is anything to go by, there is one more step you need take to switch from nvidia to default nouveau.

Only if one had created that .conf (/blacklist-kernel-nouveau.conf) and blacklisted nouveau -not something that will come up in a default install.

---

### Post by coffeecat on 2010-04-14
> **mc4man said:**
> Only if one had created that .conf (/blacklist-kernel-nouveau.conf) and blacklisted nouveau -not something that will come up in a default install.

Nope. I never blacklisted anything. It must have been Jockey when first installing the nvidia drivers. My blacklist-kernel-nouveau.conf file is dated 9th March in a system installed on 28th February from a daily build ISO downloaded on 24th February. That 9th March date would be about right because I remember running this system on the default nouveau driver for a few days before letting Jockey install the nvidia driver.

Perhaps Jockey doesn't blacklist nouveau now, but I certainly remember some talk about this then.

---

### Post by nanog on 2010-04-14
compiz *usually* works on my 8400 gs **with the edgers ppa**. 

have you tried:
```
compiz --replace &
```

---

### Post by coffeecat on 2010-04-14
> **nanog said:**
> compiz *usually* works on my 8400 gs **with the edgers ppa**. 

have you tried:
```
compiz --replace &
```

Yes, I did - no go. But thanks for letting me know that it "usually" (:)) works with the 8400GS. I'll give it another try tomorrow.

---

### Post by x-shaney-x on 2010-04-14
> **mc4man said:**
> Only if one had created that .conf (/blacklist-kernel-nouveau.conf) and blacklisted nouveau -not something that will come up in a default install.

I also have this file and have not added it myself.  

Just wondering how I would know which version of nouveau is actually enabled?
I have installed from the PPA and also un-installed nvidia common.
Ran the update-alternatives stuff and plymouth came up with the full 1680x1050 res and everything so nouveau but when I try to run compiz it says software rendering detected (as it does with the default nouveau) and won't run.

---

### Post by mc4man on 2010-04-14
> I also have this file and have not added it myself.

Maybe it was added and not removed at some point, at this point my oldest installs date to Jan. 18 and I don't have it on any of them.

(pretty much a moot point - if for whatever reason you happen to have that particular file, then obviously you'd need to comment it as coffeecat has suggested.

(now nouveau is blacklisted in another file, but that is normal (using nvidia-current here atm) and shouldn't be touched


> doug@doug-desktop:~$ cat /etc/alternatives/nvidia_modconf
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96


On a tester with nouveau and the xorger's ppa, compiz seems to be working rather poorly atm, at least with 'scroll on desktop' (cube)
It works fine until I open and close anything, then it dies, as does any other effect I enable to test.

( at least *on the hardware* I have nouveau on I think it performs better without the ppa and 3d, certainly in terms of video tearing which is minimal with nouveau, more pronounced with 3d enabled and always non-existent with nvidia


Edit: with an update just now from xorger's,  compiz is now again working well

---

### Post by x-shaney-x on 2010-04-15
Turns out I wasn't getting 3D nouveau because I had boot in to the wrong kernel :)

In my case, the performance on compiz is quite amazing and much MUCH better than I ever expected.
I copied over the compiz config files from my day-to-day linux mint install and there is very little difference running with nouveau on lucid and nvidia driver on mint.

In fact the ONLY difference I have noticed is no blur (which I don't generally use) and the odd tearing on wobbly windows and cube (I usually use wall anyway).

I had tried it on the Fedora 13 live cd and it was decent running from that but on an installed OS I am very impressed.

In fact as far as I'm concerned I am switched over to nouveau completely on lucid and will be using it on the final release.  Probably have it mostly disabled for now fo debugging other things.

---

