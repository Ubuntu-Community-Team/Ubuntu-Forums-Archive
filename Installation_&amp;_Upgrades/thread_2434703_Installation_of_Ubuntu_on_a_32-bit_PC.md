---
title: "Installation of Ubuntu on a 32-bit PC"
date: 2020-01-09
forum: Installation &amp; Upgrades
---

### Post by joearkay on 2020-01-09
**UPDATE: Have since determined that this is NOT a 32-bit processor - sorry for the misleading post title...**


Hi all, 

I'm trying to install Ubuntu onto a Protech SP-6305 Panel PC. It has an Intel Atom N2800 CPU and 2GB of RAM installed. It currently runs Windows XP perfectly, as this is what was installed when I purchased it (used). I'm having trouble installing Ubuntu. I first tried ubuntu-18.04.3-desktop-amd64 burnt to a USB and could get to the GRUB GUI to click 'Install Ubuntu'. The screen would then appear black after this. 

When selecting this from the boot menu, it showed up as 'UEFI: USB Stick'

I then tried ubuntu-16.04.6-desktop-i386 as thought I may have better luck with a 32-bit OS. The UEFI option no longer showed up in the boot menu, so I merely selected 'USB Stick' from the boot options and again I get a black screen. It's an American Megatrends BIOS. 

Does anyone have any ideas? I'm now back to 18.04.3-desktop-amd64 as that got me further than the 32-bit OS.

---

### Post by GhX6GZMB on 2020-01-09
The N2800 should support a 64-bit kernel. But 2 GB RAM is IMHO too little for Ubuntu.
Try Lubuntu instead, this will run nicely with 2 GB.

[http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/lubuntu-18.04.3-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/lubuntu-18.04.3-desktop-amd64.iso)

The installation takes time, sometimes more than an hour. If you have the option of connecting a DVD drive and installing from there, you'll have "acoustic feedback" on whether the installation is proceeding. :)

BTW: you'll need internet access after getting to the install GUI.

---

### Post by sudodus on 2020-01-09
You can find lots of tips at this link to a tutorial thread here at the Ubuntu Forums:

[Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by joearkay on 2020-01-09
I've worked with Lubuntu before and actually have it on another machine, so good shout! Results so far are bleak however! 'Run Lubuntu', 'Run Lubuntu (Safe Graphics)' and 'OEM Install' all seem to give me a black screen after selecting them. Strangely there isn't the usual 'Install Lubuntu' option either?

PS - wording on some of those options may be a little skew - AFD

---

### Post by joearkay on 2020-01-09
Ok, so as an update - on lubuntu 19.10 I click on 'Start Lubuntu(Safe Graphics)', there's a pause, and then I get `3.0067251 gma500 0000:00:02.0: GPU: Power Management Timed Out.` and then back to a black screen. I've googled this and am getting mixed results, but will post an update if/when I get any further.

---

### Post by guiverc on 2020-01-09
Did you verify your thumb-drive (live/install-media) was perfect? using the *Check disc for Defects* option (mentioned in [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html))

I write ISO's to thumb-drives most days, and having failed writes seems somewhat common, so I'd suggest confirming your ISO is perfect & write to media was flawless as that takes only minutes, instead of hours+ of subsequent diagnosis if flawed.

Possibly useful : [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0) and [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

---

### Post by GhX6GZMB on 2020-01-09
^ This.
Secondly: there are dodgy *ubuntu install sites around. Did you follow my link in post #2? Thats's the official repository.
Thirdly: I've had issues with 19.10 myself, but Lubuntu 19.04 is a marvel. Try that instead, perhaps?

The "Start Lubuntu" or" Start Ubuntu (Safe Graphics)" menu says you're not even in "Live Boot" mode. This is unusual.

---

### Post by mastablasta on 2020-01-10
try MXLinux or AntiX. easy to use and should install well on 32 bit machine.

---

### Post by joearkay on 2020-01-10
Ok, 

So to address a few bits of feedback so far (and thank you by the way!):

**Check disc for Defects :**This yields the same "GPU: Power Management Timed Out" problem as before. I've tried an alternate USB[ following the steps verbatim ]("https://docs.lubuntu.net/lubuntu_installation")

**Source of Lubuntu: **I've downloaded it from the official source and am using 19.10
[B]
[U]Other observations
[/U][/B]
When booting again this morning, I noticed that just after my BIOS splash screen, I see a quick message "Error /boot/ not found" and then the GRUB menu loads - could this perhaps be cause of the below? 

> The "Start Lubuntu" or" Start Ubuntu (Safe Graphics)" menu says you're not even in "Live Boot" mode. This is unusual.

---

### Post by slickymaster on 2020-01-10
*Thread moved to **Installation & Upgrades**.*

---

### Post by joearkay on 2020-01-10
The exact version of Lubuntu I'm trying this with is "lubuntu-19.10-desktop-amd64"

---

### Post by guiverc on 2020-01-10
> **joearkay said:**
> Ok, 
**Check disc for Defects :**This yields the same "GPU: Power Management Timed Out" problem as before.

This could mean your ISO was invalid (flawed) OR your write to media was flawed.

You should only try installing WHEN that test passes in my opinion.  If you cannot perform the test successfully on that box; you should test it on another box and if it fails there too - the media is flawed & needs creation again.  If it passes on the second box then the media is likely good & it's a problem with the kernel booting your hardware on first box (which is a very useful clue).   Currently as I see it you haven't ruled out bad install media (invalid ISO or invalid write to install media).

From your description, I'd say it's 60% that your issue is either bad download or write to install media. (If you got a messages "[COLOR=#000000]Error /boot/ not found" and [/COLOR]"[COLOR=#000000]*The "Start Lubuntu" or" Start Ubuntu (Safe Graphics)" menu says you're not even in "Live Boot" mode." *[/COLOR] then I would take that as confirmation media is flawed most likely

---

### Post by joearkay on 2020-01-10
Ok - thanks for the suggestions so far. I plugged the USB into another computer (a Lenovo laptop) and was presented with the Lubuntu splash screen. This is different from the GRUB menu I see on the panel pc, for which I'm having issues. It gives me the options: 

- Start Lubuntu
- Check disk for defects
- Test Memory
- Boot first from hard disk

Running the 'Check disk for defects' original gave me an error with 1 file. I redownloaded Lubuntu and tried again. This time, no errors. So it's likely a corrupt USB file was causing problems.

Moving back to the panel pc (which is giving me the issues), I plug the same USB into it, and am presented with the GRUB menu as previously for this computer, which gives the options: 

- Start Lubuntu
- Start Lubuntu (Safe Graphics)
- OEM Install
- Check disk for defects

Clicking 'Start Lubuntu' this time (the option I've been using previously) now flashes up some additional errors, before the same blank screen. I think we're getting somewhere though, as the errors are as follows:

Couldn't get size: 0x800000000000000e
MODSIGN: Couldn't get UEFI db list
Couldn't get size: 0x800000000000000e
Couldn't get size: 0x800000000000000e
gma500 0000:00:02.0: VBT signature missing
gma500 0000:00:02.0: GPU: power management timed out

[IMG]https://drive.google.com/file/d/1mN526SW4gr0DPTbvn6gH9XYL5ahDgY3I/view?usp=sharing[/IMG]

---

### Post by CatKiller on 2020-01-10
> **joearkay said:**
> 
Couldn't get size: 0x800000000000000e
MODSIGN: Couldn't get UEFI db list
Couldn't get size: 0x800000000000000e
Couldn't get size: 0x800000000000000e


Those errors are about Secure Boot. Either you've got it on when it should be off (or off when it should be on), or you've got it set to look for custom keys, or something like that. Each UEFI implementation is slightly different, and we have no idea what you've got things set to or the history of that machine. That's the area to look in, though.

---

### Post by joearkay on 2020-01-10
Thanks for the response. So afaik there's no option for Secure Boot in my bios. 

[Here's the overview screen for the bios]("https://imgur.com/E331vOo")

[The security tab shows no information about 'Secure Boot']("https://imgur.com/86GzGgM")

[Clicking further on this tab into the 'HDD Security Information' shows anything on this page is Disabled anyway]("https://imgur.com/c9zzHaB")

In the bios, I've disabled 'Fast Boot' and 'Quiet Boot' as I like to see as much info as possible. I know there's also issues introduced with both of these enabled. The computer currently runs Windows XP and is otherwise 'as I received it'. It was an eBay special!


[IMG]https://imgur.com/E331vOo[/IMG]

---

### Post by Dennis N on 2020-01-10
> ..there's no option for Secure Boot in my bios. 

FYI: Secure boot is a feature that's only in UEFI.

---

### Post by joearkay on 2020-01-10
I've tried booting the USB in the mode isn't prefixed with "UEFI" however I get nothing


> **Dennis N said:**
> FYI: Secure boot is a feature that's only in UEFI.

---

### Post by GhX6GZMB on 2020-01-10
Show us a shot of the Boot menu in the BIOS, please.

---

### Post by joearkay on 2020-01-11
Sure. 

In my [boot menu]("https://imgur.com/xY1smeD") I can select:

-'UEFI: SanDisk'
- 'SanDisk'
- 'UEFI: Built-in Shell' 

...or the HDD that has Windows XP installed. SanDisk is the USB that I have the ISO burned on. There's another screen [here]("https://imgur.com/ezSYsN6") that shows some 'boot override' options.

---

### Post by oldfred on 2020-01-11
My system calls Secure Boot as "Windows" or "Other" and manual says use "Other" if installing Windows 7 as it does not support Secure Boot.
So look in advanced settings tab.
Microsoft requires vendors to allow users to turn Secure boot off. At least currently.

---

### Post by joearkay on 2020-01-12
Thanks for all the help everyone. I had some spare DDR3 and a copy of Windows 7, so I've upgraded and installed that. Given that the ubuntu install wasn't as straight forward as I'd have hoped and the fact that most of the touchscreen drivers are windows...I think I'll stick with that.

---

### Post by sudodus on 2020-01-12
[Windows 7 reaches end of life on January 14 2020](https://support.microsoft.com/help/4057281/windows-7-support-will-end-on-january-14-2020), only a few days from now. It means that there will be no more security updates.

I would really recommend that you try with something else. If Ubuntu does not work well in your computer, you can try with many other linux distros. Some of them are made for old computers.

There are many good tips in the following 'megathread',

[Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640)

---

