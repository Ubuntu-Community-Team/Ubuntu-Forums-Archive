---
title: "Can't try out Ubuntu from Live CD. Nvidia?"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by rmbelson on 2010-06-23
Want to try Ubuntu and am booting from iso CD I burned. Purple screen hangs on red/white dots animation. Then error msg. "The installer has encountered an unrecoverable error.  A desktop  session will now begin so you can investigate the problem or try  installing again"

I get a black screen, so I can't do anything in the desktop session. I tried rebooting and hitting keyboard when  the boot screen showed a keyboard icon. Nothing happened.

Here is my system info:

Mainboard :    Abit AN-M2HD(MCP68)
Chipset :    nVidia GeForce 7050 PV
Processor :    AMD Athlon X2 BE 2400 @ 2300 MHz
Physical Memory :    2048 MB (2 x 1024 DDR2-SDRAM )
Video Card :    NVIDIA GeForce 7050 PV / NVIDIA nForce 630a 


Any easy workarounds? I just wanted to give Ubuntu a tryout, but if it takes huge amount of fiddling, probably not worth it until I get a new system. I assume it may have something to do with my Nvidia boards.  Thanks, rmb.

---

### Post by darkod on 2010-06-23
I'm still not used with the new menu layout in 10.04 so I might miss a bit, but look around for similar options and adjust.

When you boot and the first splash image appears, hit any key. It should show the main menu.
Hit Esc and it should show a boot line. At the end of the line add nomodeset. Press Ctrl+X to boot, or select Try Ubuntu from the menu if possible.

See if it helps to boot the live desktop without the error message.

---

### Post by rmbelson on 2010-06-24
Nope. Boot, first splash image, hit key, screen goes black and then boots to the red/white dot screen I was having before.

Tried this disk on another machine. It took ages and then booted to a screen with error messages above and command prompt below asking for a command prefaced by (subu?). I didn't note the error msg, there were 3 or 4, though one was about failure to locate cache.

 I thought Ubuntu was supposed to be easy and not ask me to know programming.

---

### Post by darkod on 2010-06-24
Sounds like a bad cd. Maybe the image file was corrupted during download, or while burning. Did you burn it at low speed, and that means 4x or 8x, not higher?

Try getting another ISO, best from torrent because it checks for corruption during download.

---

### Post by rmbelson on 2010-06-27
Made new CD at lowest speed (16x, instead of 48 as the previous one). Same result. If I can't get this to work fairly simply, I think I'll bail. Must be a conflict with something in my setup. Aren't there problems with Nvidia chipsets -- what I have, see above.

---

### Post by jnorthr on 2010-06-27
there is a 'nomodeset' option at boot time which might/mightnot fix this:
when you reboot ur system, you will see the GNU GRUB menu. Press the 'e' keyboard on ur keyboard. U should see the panel of boot options that are used at boot time. Go to bottom of that list and on the last blank line, type 'nomodeset' without quotes. Tyhen ctrl-x key combo to resume boot. Good luck.

---

### Post by ronparent on 2010-06-27
I agree with darkrod - sometimes your download is corrupted. I have also had problems with cd's burned from a dvd/cd burner - try burning the iso to a dvd. Also the nvidia live cd boot problems can usually be fixed by adding the nomodeset parameter to the end or the boot line.

---

### Post by stanley82 on 2011-05-21
I have Ubuntu 10.4-6-64 on my machine and I've updated my monitor to a new wide screen.  It looks great.
Problem, I'm trying to run a live CD with 11.4-64 and it starts okay gives me a blank screen (no signal on monitor) and boots (I think) but that's no use as I'm not able to control what's happening.  I re-tried using my old 10-4-64 CD and get the same thing.  It was okay before I changed monitors.  Any ideas?  Ian.

---

### Post by Fedorko on 2012-02-02
i think ubuntu 11.x had a problem with nvidia drivers because on ati radeon it works fine for me.

---

### Post by IndigoRage on 2012-02-02
I've only run into two kinds of problems with Ubuntu since I started playing with it circa version 7.4:

1. Bad downloads
2. Unsupported graphics

I don't know if it's the same that everyone else has mentioned, but I recall something like a "low graphics mode" that can be enabled when started Ubuntu. This has always resolved issues similar to this for me. Once in Ubuntu you can then load the correct driver for your video card and enjoy.

---

