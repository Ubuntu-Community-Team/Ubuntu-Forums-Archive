---
title: "Windows-only BIOS Flash upgrade; *WITHOUT* a Windows dual boot."
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by gurubie on 2013-09-09
You know those BIOS upgrades, that you've been meaning to do; but the installer now requires Windows, and painstakingly installed; to do it? Not this way, and you can still use the "official installer". Step by step. This way works.

NOTES: Mine is a (Debian GNU/Linux 7 Wheezy/Stable; with a custom, Mate/stable desktop only. Ubuntu in VB etc..), **HP model dv9000 (dv9225us) laptop (bad heat design)**, and HP *only* provides one type of BIOS download, and its **strictly Windows only!** NOT DOS. Its one *.exe download file, **fails in DOS**. All, typical DOS (and hold keys), BIOS upgrade methods failed; including an HP_TOOLS named volume, and only the Windows type BIOS upgrade flasher is officially supported. DOS, or even Linux BIOS upgrading should be technically possible; but here, it's EXPERIMENTAL, not supported, and easier to brick your computer. not what you want, for BIOS upgrading.

Dual booting Windows is great for seeing; but it gets old, and it's convoluted. Windows is history.

I went from a F.3 to the F.43 BIOS version, on my laptop. This fixed SD card issues, fan control, and Win 7 stuff. **Always know why you are risking a BIOS upgrade.** It's usually OK; but use at your own risk. My method here offers a proper, MATCHED, safe, BIOS upgrade process, closest to official, including auto BIOS backup. 

Make sure never to use the wrong BIOS.

I frakin' did it. LOL. Whew. Worst BIOS upgrade ever!

This guy...

[http://techblog.sagar.se/blog/2010/06/11/upgrading-the-bios/](http://techblog.sagar.se/blog/2010/06/11/upgrading-the-bios/)
 
...went through all the various methods(summary); that I did. Its kinda amusing to read. God bless him! Including a SUCCESSFUL BIOS UPGRADE..

My, more detailed, steps:

**On Gnu/Linux:**
> Hiren's BootCD (HBCD) download [http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/) , and installed on a fast (writable/booting) USB was created. Comp set to boot USB. 
(I used Multisystem; for drag, and dropping the iso to USB, boot able install. That's just one way.) 

[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

**Next Note: Just  running the non-extracted executable (on default Live Mini XP) required XP admin  privileges; that can't change, with Hirens live XP, in its current form, fails.  Ironically, You can't use its own Windows utilities on itself, and it  doesn&#8217;t logout, or in, to get root/admin. **

> EXTRACT (right click; extract here) the damn HP Win only (*.exe) BIOS, downloaded file (Your **MATCHED** one, from HP).

### Skip this but do not run it; until you do this below!
#
#Go inside your newly extracted BIOS folder....
#
#Rename the actual BIOS file, such as... *#numbers#.WPH*  (in may case), to **BIOS.WHP** *and* copy it into the  non-64 bit (of the two) **sub**-folders (replacing the BIOS.WPH that's in there); so to be used for the Windows NT 32 only, BIOS program (exe) loader, in there.
###Skip end
> Copy the extracted folder onto the Hiren USB drive.

Boot Live:

Boot your USB drive > Run grub4DOS > Hirens HBCD > and Mini XP (multi tries?), and then, from a Windows (32 bit) NT/XP (live mini)
> Change directory into you newly extracted BIOS folder. **Don't run it yet!**

***If you forgot to rename, and move, your correct BIOS, you can run flash32.bat in there, and as it does the same thing.

Then go into that **sub**-folder (not the 64bit Vista one), and simply execute the Windows NT/32 Flashing program there. It's Swinflash.exe, or somthing like that. It uses your new, carefully matched BIOS; that you put in there. **Not the BIOS.WPH that was there! **
> Then  finally, we get a beautiful (Win GUI), no nonsense, descriptive, hand  holding, easy, clear, fast BIOS upgrade install(with instructions); without flying blind,  and praying you don't brick the thing. It was fast, and clear, at every  step.

After reboot, my BIOS reports the new version! Plus now you now have Live XP, and recovery tools. The best rated one.  

END #################################################### DONE

Other ways (that **didn**'t work for me) to do this (Without a Windows install). 

1.  The HP hold-down, of the WinKey+B, during power ON, and with the right  files, on a (no boot-able needed) USB drive, did NOT work (would have been nice), and you can't  see anything! It was much less official, and risky. It's easy to brick. This method was  historically used to restore the OLD BIOS, if it got bricked, from the OLD,  now gone, "HP_TOOLS" volume partition, originally on the hard drive. No matter. A (correctly  prepared) USB stick, does the same thing, HP says. But they do not offer  the exact files, or instruction. The key sequence is reported to be difficult to activate,  and requires numerous tries. One can't tell if its started! I did see  it work, on my model, on Youtube. However, mine did not make that  mode/sound, and I think it rejected the (same renamed) files, from the extraction, that  I ultimately upgraded, with Mini XP above

2. I tried another "XP LIve" CD I found and it sucked bad.  It seems like it was pretending, and I bet, it might have hacked any  given Windows partition, if I had one.

3. My first  build of a Bart PE failed (the other win to go stuff stinks), and required another Win CD; but that guy in  the link said it didn't work for him; even with a working, homemade  (legal) build of Bart PE live XP. I never tried getting a Bart PE, already done,  and that would be risky, and perhaps not universal.

4. Most interestingly, there's this...

[https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux](https://wiki.archlinux.org/index.php/Flashing_BIOS_from_Linux)  

...and that replaces Windows-only BIOS installing, *if* I could  be sure which files (and their naming) are the proper ones to use, of  the ones the HP Win Flasher used. It's definitely more official, to use the  only method; that HP provided.

5. Flashrom said it should **not** even **read** the BIOS first, as that could corrupt it. ???

6. The (DOS) BIOS, hack tools, on the same Hiren HBCD, are "officially" not safe, for flashing; nor matched to my system. It was very low confidence, for flashing this model. 

-----
I suspect HP wouldn't think we could do it, with a (thought impossible) Live  XP, and at least after extracting, and renaming the right parts, in the right  folder, and running it from that folder. Shameless anti-competitiveness, if you ask me. 

HP sucks! The hardware design, the support, and the attitude. ...Way to destroy your brand.

 **HARDWARE NOTES:**

Other than the fan, these are largely unrelated to BIOS upgrading.

BTW, this HP laptop still doesn&#8217;t want to come ON, sometimes, but I  can now get it to, usually within 10 minutes, or less. So it's usable, and its  very, custom setup. It's a very bad design, and I'm not disassembling it a third time! **Some heating can be done without any dis assembly.** People actually put the back vents into a pillow, to bring it back. It does have heat-limit safety shutdown. But warming it, is **only** because it was a complete loss/boat anchor to me. It's counter intuitive. All that will eventually kill it. A  replacement motherboard is cost prohibitive, and DOES have the same  issues. The hot AMD CPU's messes, with its, and/or Nvidia's GPU  soldering. It gives a check-sum error (loud beep code) and will not POST,  sometimes. Known issue; that HP hasn't made good on. The HDD, and RAM, runs hot too. With my new copper, GPU heat-sink  mods, all it's within (high) tolerance, according to the sensors. 

FYI

---

