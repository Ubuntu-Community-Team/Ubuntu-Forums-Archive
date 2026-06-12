---
title: "Editing Grub to solve blank screen problem"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by grey1beard on 2011-06-26
I have been running Lucid on a Toshiba Satellite A30, and want to upgrade to the next LTS, 10.04, even though I knew I would have problems with the graphics(onboard Intel 855GM chip), but I bit the bullet, updated everything via update manager, then hit the upgrade button.

Currently, the graphics are working in low resolution mode, and, having read through the *Ubuntu 10.04 “Lucid” Blank Screen at Startup : Workaround* I assumed I could edit Grub to add the entry "i915.nomodeset=0", but cannot discover how to get at it.
I can't find the grub file in the file system, even with hidden files shown.
Can someone tell me how to find it, or if I can add the line through Terminal ?

As an old newbie, I'd appreciate a full how-to ;)
John

---

### Post by grey1beard on 2011-06-26
I've now found the grub/menu.lst which is where I assume I need to add the instruction, as above "i915.nomodeset=0", and just type it in after the "quiet splash" entry ?
Is this correct ?

John

---

### Post by foresthill on 2011-06-26
This should get you started. To edit grub, use this command:

[PHP]gksudo gedit /etc/default/grub[/PHP]

When you're done, use this command:

[PHP]sudo update-grub[/PHP]

---

### Post by foresthill on 2011-06-26
Also, if you want to test out certain grub modifications, reboot and select 11.04 in the boot menu, hit your "e" key, add the code, hit escape, and hit then enter to resume booting.

Modifications entered in this way will go away the next time you boot up, which is good for testing purposes.

---

### Post by grey1beard on 2011-06-26
Hi foresthill, and thanks.
If I type *gksudo gedit /etc/default/grub* gedit gives me a blank window, but if I use *gksudo gedit /boot/grub/menu.lst * I get the file I mentioned in #2.
Advice ?
Thanks
John

---

### Post by oldfred on 2011-06-26
Is this an upgrade from an older install 9.04 or before? Then you probably are running grub legacy unless you explicitly upgraded to grub2. If you have menu.lst and no[COLOR=#000000][COLOR=#0000BB] [/COLOR][COLOR=Black][COLOR=#007700]/[/COLOR][COLOR=#0000BB]etc[/COLOR][COLOR=#007700]/default/[/COLOR][/COLOR][COLOR=#0000BB][COLOR=Black]grub[/COLOR] [/COLOR][/COLOR]  or you most likely are still using grub legacy.

If you only have Ubuntu, you get the grub menu on reboot by hitting escape right after BIOS. With grub2, you hold down shift key until menu appears. Then you can use e to edit grub boot line. But that is a one time change to test if it works. Then you can update menu.lst. You add additional parameters after splash quiet. If you want grub to include it on updates you have to edit the parameters at the top of the menu.lst as the entires in the automagic area are rewritten on grub updates. 

In grub2 [COLOR=#000000][COLOR=#0000BB] [/COLOR][COLOR=Black][COLOR=#007700]/[/COLOR][COLOR=#0000BB]etc[/COLOR][COLOR=#007700]/default/[/COLOR][COLOR=#0000BB]grub [/COLOR][/COLOR][/COLOR]is similar to the top part of menu.lst to let you set parameters. The automagic area is similar to the grub.cfg file as it is rewritten on every update. And 40_custom is similar to the area after (or before as 05_custom) the automagic area to let you add additional boot stanzas.
[COLOR=#000000][COLOR=#0000BB][/COLOR][/COLOR]

---

### Post by MAFoElffen on 2011-06-26
> **grey1beard said:**
> Hi foresthill, and thanks.
If I type *gksudo gedit /etc/default/grub* gedit gives me a blank window, but if I use *gksudo gedit /boot/grub/menu.lst * I get the file I mentioned in #2.
[COLOR=Red]Advice ?[/COLOR]
Thanks
John
Have you looked at the first 3 posts of this sticky?
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

Even though it was written for Grub2 and later Versions of Ubuntu, KMS was implemented in your version.  Some of the filenames are different, but most of the KMS switches and Xorg configuration files are the same.  Just ideas to try that help diagnose and that affect graphics...

Has a lot of info and instructions for what you are trying to do.  I'm currently trying to update the first 3 posts to move what is current as workarounds and fixes from the rest of the thread, into those first 3 posts... So people don't have to weed through the whole thread to find things.

Also-- In My Honest Opinion, any question about Legacy Grub, Grub2 and LILO... oldfred is definitely "the man" to go to!

---

### Post by grey1beard on 2011-06-26
Hi oldfred.
Thanks for the additional info. I take it the "automagic area" is the top section where all the line have multiple hashes in front of them.
(Who comes up with these names, I wonder :D )

I've just discovered that I've been mixing up "nomodeset" and "i915.modeset", probably typing "i915.nomodeset=0"so I'll have to start over.:(

John

---

### Post by grey1beard on 2011-06-26
Hi MAFoElffen.
Yes I have read that thread of yours several times, and quite a few others.
Being a bit long in the tooth, and still very much the newbie, I do find the fact that there are so many small, but important variations in the particular set ups that everyone has more than a little confusing.

I guess we would all like a simple path to follow, but I know how useful all experience is, even though at the time it seems like a cul-de-sac.

Plodding on,
regards to all,
John

---

### Post by oldfred on 2011-06-26
In menu.lst about a third of the way down should be this:

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

Then near the bottom is the end automagic. You are only supposed to write before or after the automagic as it is auto rewritten. The area above the start of the automagic is the settings and configurations are in the automagic with only one # and comments are multiple ##. Do not change # itself but just the setting after it.

You should find a section like this:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash quiet

and anything after the splash & quiet will be added to the kernel line like splash quiet are added now on every update to grub. You can add it manually but if you do not also update the defoptions line the next update of grub will not then have it.

Both grub legacy & grub2 use this to update menu.lst or grub.cfg.
sudo update-grub

---

### Post by grey1beard on 2011-06-26
Oldfred, I forgot to say that I'm upgrading from 8.04 to 10.04.
Many thanks for the info on automagic. Things are slowly dropping in to place, even though it's like learning another language - not a strong point for me.

John

---

### Post by grey1beard on 2011-06-26
Made it ! Well, progress at least.

Continuing with my reading, I found a thread *"Working Intel driver for 82852/855GM"* and I decided to try the Stefan Glasenhardt ppa.
Never having tried a ppa before, it took me a little while to discover that, though I had run sudo apt-get update, it was only updated when I ran the update manager.
I can now run in normal high resolution mode, so that's a great start.

I'll leave it now till tomorrow, and if all goes well, I'll mark the thread solved.
Night all, and many thanks,
John

---

### Post by MAFoElffen on 2011-06-26
> **grey1beard said:**
> I've just discovered that I've been mixing up "nomodeset" and "i915.modeset", probably typing "i915.nomodeset=0"so I'll have to start over.:(

John
That really all depends on what video chipset you are using. " i915.nomodeset=0' is specific to some intel chipsets.  "nomodeset" is specific to nvidia chipsets )and a few others). "radeon mode=0" is specific to ATI Radeon chipsets...

The kernel has particular switch settings specific to the kernel version and the kernel's graphics modules "it" loads.  There are "other" kernel switches that are particular to other graphics drivers and modules that are loaded during Xorg.  Those switches are documented with the specific video drivers.

The easiest way to figure out which video chipset you have (and will point to the kernel modes you might need to use) is to open a terminal and:
```

lspci -v | grep VGA 

```That will list the video chipsets that Linux sees through the PCI bus.

Edit- Sorry, that assumes that you can get to a text console or terminal session... i.e. like via using a "text" kernel boot switch.

---

### Post by grey1beard on 2011-06-27
Good morning MAFoElffen, and thanks for your help. Your thread mentioned above has given me a boost up the learning curve.

Now that it seems to have settled into it's new version, a brief summary.

Originally running Hardy Heron 8.04 LTS on a Toshiba Satellite A30 with onboard 855GM chip.
Using the upgrade manager to go to Lucid Lynx 10.04 LTS only produced a blank screen after the initial Ubuntu splash screen appeared for about 1 second.

Editing the grub menu produced no improvement, and the final solution was to use Stefan Glasenhardt's ppa to be found at [[COLOR="Blue"]https://launchpad.net/~glasen/+archive/intel-driver[/COLOR]]("https://launchpad.net/~glasen/+archive/intel-driver") .

Having downloaded the ppa, I found it necessary to run Update Manager to get the package working.
All is now well, and seems to be running smoothly.
Many thanks to all.
John

---

