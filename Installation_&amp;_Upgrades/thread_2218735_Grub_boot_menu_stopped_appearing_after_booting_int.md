---
title: "Grub boot menu stopped appearing after booting into Windows 8.1"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by Keilan on 2014-04-21
Hey everyone,

This is my first post here, so my apologies if it isn't in the right place. I've been using a laptop given to me by my employer that dual-boots windows 8.1 and Ubuntu (13.10 I believe). The vast majority of the time, I use Ubuntu (and select it from a grub menu), but last week I booted into Windows, used some windows only programs, and restarted - at that point everything worked fine and I booted into Ubuntu again and continued as normal. However, when I turned it off, Windows installed a LOT of updates - I assume one of them is what cause the problem. Today I logged into Windows again, and now I cannot get back to my Ubuntu partition. No matter what I do, it goes right back to the windows start screen, bypassing grub and not even giving me a chance to open the bios. I'm not very good at this sort of thing, but what I've attempted so far is:

1) Turn off Windows fast start, and hibernate options
2) Try to access the bios by spamming F1, F2, F11, and DEL when the computer starts (no response, and it doesn't even seem to display a post screen)
3) Restart windows using "Advanced startup" to go into the UEFI menu, and disable Secure start
4) Download a boot-repair ISO, burn it using FreeISOBurner, and switch the DVD drive to boot option 1 in the UEFI menu, but on restart the disc is not recognized

So in short, I haven't been able to make any progress on doing anything besides standard windows booting, and I believe it is because of Windows 8.1 Update. Any guidance on how to get back to my Ubuntu partition would be hugely appreciated.
-Keilan

---

### Post by dsc1596 on 2014-04-21
Keilan,
You may try using an ubuntu live cd, but I imagine if the boot-repair iso doesn't work, then that won't either. Sounds like access to the BIOS or at least the boot menu needs to happen to make any progress. Try looking up the laptop model on the manufacturer website, or even just googling the model and 'boot up key', sometimes that works. I notice you didn't include the 'esc' key in the list above, you may also try that.

---

### Post by Keilan on 2014-04-21
Hey dsc1596, thanks for replying. I tried using ESC and didn't have any luck - googling for Toshiba P50-A boot key didn't give me any keys to try, just suggested I make sure I'm not going into hybrid-shutdown mode, which I think I disabled by disabling fast startup. I'll try burning a live CD tomorrow and seeing if I have any luck with that.

---

### Post by dsc1596 on 2014-04-21
[Here]("http://ubuntuforums.org/showthread.php?t=2195819") is a thread with a similar problem to yours, but that one was not resolved yet either. [Here]("http://ubuntuforums.org/showthread.php?t=2214323") is another thread that seems to have been resolved when an option called "nomodeset" was used, but that one seems video related, so may not be the same issue you are having. [This thread]("http://ubuntuforums.org/showthread.php?t=2163854") may also be useful as well, looks like the OP had to turn off the NIC and then boot from USB with secure boot disabled but with EFI boot on. [This site]("http://forums.toshiba.com/t5/Satellite-Laptops-all-other/toshiba-satellite-p50-a-11-L-DVD-CD-not-working-and-do-work-less/td-p/525507") claims that F2 should work to get into the BIOS. Good luck, hope something here helps.

---

### Post by fantab on 2014-04-21
> **Keilan said:**
> .........No matter what I do, it goes right back to the windows start screen, bypassing grub and not even giving me a chance to open the bios. I'm not very good at this sort of thing, but what I've attempted so far is:

1) Turn off Windows fast start, and hibernate options
2) Try to access the bios by spamming F1, F2, F11, and DEL when the computer starts (no response, and it doesn't even seem to display a post screen)
3) Restart windows using "Advanced startup" to go into the UEFI menu, and disable Secure start
4) Download a boot-repair ISO, burn it using FreeISOBurner, and switch the DVD drive to boot option 1 in the UEFI menu, but on restart the disc is not recognized

So in short, I haven't been able to make any progress on doing anything besides standard windows booting, and I believe it is because of **Windows 8.1 Update**. Any guidance on how to get back to my Ubuntu partition would be hugely appreciated.


Yes, Windows updates are known to rewrite the EFI files and other sytem settings to the default Windows settings. (I am assuming you have UEFI with EFI System Partition [ESP]).
[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") is the easiest option to fix boot.

Boot with Ubuntu DVD/USB-> Try Ubuntu [without Installing] -> Now install Boot-Repair from Terminal:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update 
sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list" 
sudo apt-get update 
sudo apt-get install -y boot-repair && (boot-repair &)
```

This will install BR to the booted Live Ubuntu. This is only temporary. If you reboot then you will have re-install BR again.

Run Boot-Repair and '*create a boot-info summary*'. _Note the url link_ created for the bootinfo report.
Run '*Recommended Repair*'... again make a note of the new bootinfo summary url link.
In your UEFI change HDD boot order to Ubuntu.

Reboot... 

If you still have problems booting Ubuntu then post the url links of the two bootinfo url links here.

---

