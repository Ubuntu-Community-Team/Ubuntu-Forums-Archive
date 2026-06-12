---
title: "Recommendation for a technician in Geelong? upgrade from 10.4 to 12.4 went wrong"
date: 2014-07-09
forum: Installation &amp; Upgrades
---

### Post by eternity*7 on 2014-07-09
Was upgrading from 10.4 to 12.4 and something major went wrong. can't get past the first error message and now need someone who knows what they're doing to fix the data and retrieve data.

---

### Post by Bucky Ball on 2014-07-09
*Thread moved to **Installation & Upgrades**.*

Can't be of much help with so little information. ;)

The error message(s) would be a start ...

If you simply want to retrieve data, boot from the LiveCD/USB, plug in an external drive and back up your data.

For what it's worth: a backup and clean install is often less problematic. 10.04 is fourteen months out of support, so not sure if that method of updating is still going to work anyway. If you do get it to work, untick all manually added PPAs prior to the upgrade.

We no longer support end-of-life releases here, but as you are attempting to upgrade, we'll let it slide for now. FYI:

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

I do recommend the clean install of 12.04 LTS or 14.04 LTS, though. A LOT changed from 10.04>12.04.

---

### Post by eternity*7 on 2014-07-09
Was upgrading from 10.4 to 12.4 as read that shouldn't go straight to 14.
The error message is :
init:udevtrigger main process (402)terminated with status 1

Where do I find a live cd/USB?

This problem started when I couldn't save to a USB or external hard drive. Realized that on old version so thought it was best to upgrade first. Now have a much bigger problem.

---

### Post by Bucky Ball on 2014-07-09
? [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

12.04 and 14.04 are both long-term support releases and that now means five years support.

---

### Post by eternity*7 on 2014-07-10
Thanks - have done that. Managed to download ubuntu onto a USB but nothing happens when try to boot. Goes to the error screen as before.
Went into boot info and USB at top of boot priority list but in [] note sees that if in parentheses then disabled. Can't work out how to remove the []

---

### Post by sudodus on 2014-07-10
With 10.04 LTS installed, I guess your computer is old. Please specify it, and we can help you select a suitable flavour of Ubuntu, if the computer is too old or has too slow CPU or too little RAM for standard Ubuntu.

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

See also these links
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.[/URL]

[Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by eternity*7 on 2014-07-10
Custom built desktop
Intel Core 2.9G
E6500 Processor
4G RAM
4350 video card
No wifi card- external modem

---

### Post by sudodus on 2014-07-10
1. A ***pentium dual core CPU***, ***lots of memory***: This computer should run with standard Ubuntu and run well with Xubuntu.

1. I guess a 4350 video card a ***Radeon HD 4350*** card? I have little experience of Radeon cards, but sometimes the built in drivers work, sometimes a proprietary driver works, sometimes there are problems. You might have better luck with Ubuntu 12.04 LTS than with 14.04 LTS, but I'm not sure, and [COLOR=#ff0000]I hope someone with experience of Radeon cards will chip in and help you[/COLOR].

3. Can you check if there is an updated BIOS program for your motherboard?

---

### Post by Bucky Ball on 2014-07-10
Run:

```
sudo lshw -C video
```

Do you see a product line something like:

```
product: RV710/M92 [Mobility Radeon HD 4530/4570/545v]
```

Post the whole output, please. At the bottom of that readout you should see something like this:

```
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: **driver=radeon** latency=0
```

What does your driver entry say?

---

### Post by eternity*7 on 2014-07-10
Not sure where to run this.
When I turn the computer on I have the following options:
1. First screen- option to enter Bios or Set- up
Bios - can't see where  in here to run command
Set-up - quickly displays lines of commands that are so quick I can't read it and then goes to screen 2.
2. Normally let it go to next screen where have options to select Ubuntu including recovery versions and Windows. All Ubuntu options including recovery result in same next screen.
3. Next screen displays message 
The disk drive for / is not ready yet or not present. Then have 3 options, wait, skip or manual mount. The wait option does nothing. The skip option goes to the message 'the disk drive for tmp is not ready yet or not present. The manual option brings up script with the final line  the modprobe: FATAL error message.

---

### Post by eternity*7 on 2014-07-16
Went to a professional who was able to get it going again but found that all the data had been corrupted. Some leakage also across into the Windows side. Now have new version of Ubuntu with all data lost-AARGH! 
Hopefully this will be helpful in stopping others going through the same pain.

---

### Post by Bucky Ball on 2014-07-17
Please mark thread as solved. Despite the fact it has been disastrous, your original issue no longer exists.

---

