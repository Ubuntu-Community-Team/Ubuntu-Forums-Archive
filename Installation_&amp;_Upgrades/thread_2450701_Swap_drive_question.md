---
title: "Swap drive question"
date: 2020-09-18
forum: Installation &amp; Upgrades
---

### Post by adrenalizd on 2020-09-18
Hello everyone,  I have a question about the swap drive.  I haven't used Linux since back in college in the late 90s. From what I remember we used to set the swap drive as double the ram.  Has anything changed? I am getting ready to set mine up and I feel 128gb for a swap drive might be a little excessive.  Thank you so much for your replies!!

---

### Post by CelticWarrior on 2020-09-18
Welcome.

Yes, almost everything changed. That old rule of "double the RAM" was valid when we had very little of it. Although it's still recommended to have same swap, if you have 64GB RAM you probably won'r ever use swap.
And the next thing that changed recently is the swap partition is no longer needed. Ubuntu now uses a swapfile by default.

In summary, you can completely forget about swap. Use the entire drive for your other partition(s). Ubuntu will create the standard dynamic swapfile in the root partition. That's all you need.

---

### Post by adrenalizd on 2020-09-18
That is awesome!! Thank you!! I am looking forward to using it again, I picked up a 500 gb evo to put it on and I was worried about using that much for a swap. Wow!! It sounds like the install will be a lot easier than the old days too...lol

---

### Post by TheFu on 2020-09-18
There was a long thread here about swap sizing a few months ago. Lots of opinions. Lots of knowledge shared. You should seek that thread out and review it.
It depends on workload, but my general answer is:
* use a swap partition or swap LV
* size of the partition should be 4.1G for all desktops; many reasons this works for large RAM and small RAM desktop systems.
* don't use hibernation, ever.

I'm anti-swap file, especially since we've had GPT partitioning for over a decade. There a different opinions about this and local requirements can overrule.

The rules for servers are completely different. In general, server RAM installs should be sized to never need any swap. There are times when huge amounts of swap are desired - say you are a cheap-ass web hosting company and want to encourage the bottom-end customers to upgrade.  Then you want to force lots and lots of swapping so performance is terrible. The goal for all the cheap plans is to get people to sign up, then move to more expensive plans. It is called "business."

---

### Post by adrenalizd on 2020-09-18
Thank you!!!! I will look that up,  if nothing else just to learn.  This isn't a server or anything.  I do a lot of photography and want to get into video editing.  My 8 year old Mac is reaching the end of its life cycle and I have been using my old windows laptop for ac while so when I built this one I over built it some so that I wouldn't have to worry about upgrading to much in the next couple of years.  I put a Ryven 7 3700x with a rtx 2060 and 64 gb of Corsair Vengeance RGP Pro with a 1tb evo 970 for the windows drive and i just picked up the evo 860 500gb for the Kubuntu install.  I also have a 10tb hdd for files.  I just miss playing around with Linux and the terminal.  I may do some light gaming and from what I read it should be fine for that.

---

### Post by CelticWarrior on 2020-09-18
> [COLOR=#000000]I put a Ryven 7 3700x with a rtx 2060 and 64 gb of Corsair Vengeance RGP Pro with a 1tb evo 970 for the windows drive and i just picked up the evo 860 500gb for the Kubuntu install[/COLOR]
Use the latest release only - you may even need to install a newer, experimental kernel - and UEFI mode. Tha means among other things that if you're manually partitioning you need to have GPT and create the ESP (EFI System Partition) before any others (a ~512MB FAT32 formatted partition in the beginning of the system drive).
Disable Secure Boot and Fast Boot in UEFI.
Enable AHCI mode for drives if not the default.
Make sure to select the option to install third-party drivers, etc. (or install proprietary drivers later) for that Nvidia.

> [COLOR=#000000]I may do some light gaming and from what I read it should be fine for that.[/COLOR]
Sure. If it's capable of heavy gaming it can also do some light gaming :biggrin:. What I'm saying, in a nutshell, is your hardware :guitar: (rocks). Don't be shy using it.

---

### Post by TheFu on 2020-09-18
> **adrenalizd said:**
> Thank you!!!! I will look that up,  if nothing else just to learn.  This isn't a server or anything.  I do a lot of photography and want to get into video editing.  My 8 year old Mac is reaching the end of its life cycle and I have been using my old windows laptop for ac while so when I built this one I over built it some so that I wouldn't have to worry about upgrading to much in the next couple of years.  I put a Ryven 7 3700x with a rtx 2060 and 64 gb of Corsair Vengeance RGP Pro with a 1tb evo 970 for the windows drive and i just picked up the evo 860 500gb for the Kubuntu install.  I also have a 10tb hdd for files.  I just miss playing around with Linux and the terminal.  I may do some light gaming and from what I read it should be fine for that.

And for backups?  Seems you've completely forgotten the most important part for any system holding data you actually care about. Backups. Automatic, daily, versioned, tested, backups.

On a system like that, I wouldn't dual boot. I'd run Windows inside a VM.  Heck, I have a lessor system and run Windows .... inside a VM.

Really new hardware like that can see some issues that haven't been well solved.  I like to get stuff that is at least 12 months old, but I do my homework before any purchases to ensure I'm not bleeding edge with 1000 cuts on day 1.

---

### Post by adrenalizd on 2020-09-18
Hello everyone!! I followed your advice and the install went as smooth as can be!! It is recognizing all of my hardware and seems to be working to full capacity! I haven't had a new computer in years and I am blown away!! It is fast, almost too fast if you can believe it! I have to figure out how to slow the mouse down because everything flies and when I try to use the scroll wheel I am at the bottom of the page before I even get a chance to slow down. 

Backups are super important I completely agree, I use an offsite cloud backup for all of my photos, but I will most likely pick up another local backup before too long. That is a good idea! I didn't load a bootloader for Windows and for Ubuntu, I just installed each on their own drive and use the bios to select which one to boot into. I really appreciate all the help and look forward to learning so much from everyone!! Linux has come a long way since I used it back in the late 90s. I went with the Kubuntu flavor, as I have always been partial to KDE.

---

### Post by adrenalizd on 2020-09-19
It appears the only glitch I have at all is that the leds on the ram chips are out of order.

---

### Post by tea for one on 2020-09-19
> **adrenalizd said:**
>  I didn't load a bootloader for Windows and for Ubuntu, I just installed each on their own drive and use the bios to select which one to boot into.

Excellent choice - This is the best way to dual boot on modern systems.

---

### Post by grahammechanical on 2020-09-19
As for the mouse speed go to System Settings>Details>Mouse & Touchpad and you will be able to move a slider to slow down the mouse.

Regards.

---

