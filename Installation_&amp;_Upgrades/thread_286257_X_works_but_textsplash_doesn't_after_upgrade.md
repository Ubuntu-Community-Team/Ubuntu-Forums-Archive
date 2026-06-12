---
title: "X works but text/splash doesn't after upgrade"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by ZagiFlyer on 2006-10-27
When I first upgraded from dapper to edgy and rebooted, everything looked fine until the splash screen was supposed to come up. That is, I saw grub do it's thing and I saw the kernel start to load, then the display (Dell 2005FPW panel connected to ATI X700 card) went blank. I was, of course, overjoyed.

I rebooted the system (blindly typing chars at the KB) and restarted in recovery mode. This worked - I was able to boot to the #.

I then determined that my xserver was jacked up and fixed it. At this point when I started the system, I still got a blank screen during boot, but when X started, it came back. 

So at this point I have a usable system, but startup and shutdown don't have any display at all. I suspect this has something to do with the video mode that the splash uses, but I can't seem to get any farther than that.

Any ideas?

---

### Post by mykmelez on 2006-10-27
I had the same problem.  I mostly fixed it by following [step 6 of the usplash customization howto]("https://help.ubuntu.com/community/USplashCustomizationHowto#head-3f1a5b3bcea03e357b466d0f04f41bfe01d1f8bc"), using 1024x768 (i.e. vga=791) as the resolution.

Now the splash screen is back and displays the Ubuntu logo plus the progress meter.  But it still doesn't display any text status messages.  I have started [another thread]("http://ubuntuforums.org/showthread.php?t=286283") on that problem.

---

### Post by Ludwik on 2006-10-27
I have similar problem, but mykmelez's answer didn't help. I see black screen during whole boot time. When I tried vga=791, I've got error message saying that such vga mode doesn't exist.

PS: Sorry for my English, I'm from Poland.

---

### Post by Midway on 2006-10-27
That trick didn't work here as well :(  But as fast as it boots and shutdown I don't know if I will really miss it, lol.

I am just happy this seems to be the only problem I have from the upgrade.  Mine was interrupted about 3/4 of the way through and I thought I had borked my system.

---

### Post by frankelr on 2006-10-27
My 6.06 worked and still worked, but 6.10 shows "video out of range" from kernel start to graphical start. fooling with vga = xxx
doesn't help here. System works in rescue mode

Bob

---

### Post by kelp on 2006-10-27
I have the same problem. The image that appears in my usplash is this:

[http://aceitunassinhueso.com/images/usplash.JPG](http://aceitunassinhueso.com/images/usplash.JPG)

---

### Post by mykmelez on 2006-10-27
> **Ludwik said:**
> I have similar problem, but mykmelez's answer didn't help. I see black screen during whole boot time. When I tried vga=791, I've got error message saying that such vga mode doesn't exist.

Did you try any of the other resolutions listed on that page?

---

### Post by Midway on 2006-10-27
I tried all of those resolutions but no usplash.  I didn't have a splash either but I was able to manually install the new one.

I think the reason why I am not getting a usplash is because there was no image installed:

mitch@mitch-desktop:~$ sudo update-grub
Password:
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
**Searching for splash image ... none found, skipping ...**
Found kernel: /boot/vmlinuz-2.6.17-10-386
Found kernel: /boot/vmlinuz-2.6.15-27-386
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Maybe if someone can post this Edgy usplash image maybe I can install it.

---

### Post by erichnewell on 2006-10-27
Check /boot/grub/menu.lst and see if the word "splash" appears on the "kernel" line. If you are seeing the cursor blink then you are already at a workable resolution.

---

### Post by mykmelez on 2006-10-27
> **Midway said:**
> I think the reason why I am not getting a usplash is because there was no image installed:

...
**Searching for splash image ... none found, skipping ...**
...


The splash image referred to in this message is the grub splash image, which is completely separate from and unrelated to the usplash image.

---

### Post by sloggerkhan on 2006-10-27
Hey, just a question. Are your consoles showing up on the correct screen? Ever since I've switched to edgy, my ctrl-alt f1-f6 consoles have shown giberish. I'm wondering if they're set to display on another screen? How could I tell?

---

### Post by Midway on 2006-10-27
> **mykmelez said:**
> The splash image referred to in this message is the grub splash image, which is completely separate from and unrelated to the usplash image.

Ok, noted. I just added the "defoptions=" part that Uranus65 just posted on another thread.  Before I was just adding the VGA=7xx.  Now I have a usplash screen.  It has a black background with the Ubuntu logo and text in black outlined letters (just like the logo/name at the top of the forums) with an orange progress bar with the text scrolling underneath.  Is this Edgy's usplash?

---

### Post by mykmelez on 2006-10-28
> **sloggerkhan said:**
> Hey, just a question. Are your consoles showing up on the correct screen? Ever since I've switched to edgy, my ctrl-alt f1-f6 consoles have shown giberish. I'm wondering if they're set to display on another screen? How could I tell?

Yes, my consoles are all showing up on the correct screen.  One way I can tell is that the console identification string above the username prompt says which tty I'm on.  The one for ctl-alt-f1 says "tty1", ctl-alt-f2 says "tty2", etc.

---

### Post by mykmelez on 2006-10-28
> **Midway said:**
> Ok, noted. I just added the "defoptions=" part that Uranus65 just posted on another thread.  Before I was just adding the VGA=7xx.  Now I have a usplash screen.  It has a black background with the Ubuntu logo and text in black outlined letters (just like the logo/name at the top of the forums) with an orange progress bar with the text scrolling underneath.  Is this Edgy's usplash?

Sure sounds like it.  I have the same thing, except that I don't have the text scrolling underneath.  The relevant line in my /boot/grub/menu.lst file is:

# defoptions=quiet splash vga=791

---

### Post by Ludwik on 2006-10-28
This answer doesn't seem to work for me. But I'm not sure where should I add this line in menu.lst. Could you show me where exactly?

---

### Post by Ludwik on 2006-10-28
> **Ludwik said:**
> This answer doesn't seem to work for me. But I'm not sure where should I add this line in menu.lst. Could you show me where exactly?

Ok, I understand now, but this doesn't help. Now I got "you passed an undefined mode number" every time I boot.

---

### Post by Ludwik on 2006-10-28
Maybe I should add, that I have graphic card integrated with my Intel G845... mother board.

---

### Post by mykmelez on 2006-10-28
> **Ludwik said:**
> Ok, I understand now, but this doesn't help. Now I got "you passed an undefined mode number" every time I boot.

The usplash customization howto lists four different possible resolutions:

640x480/vga=785
800x600/vga=788
1024x768/vga=791
1280x1024/vga=794

Perhaps the one you tried isn't supported by your video card.  Try one of the others and see if that one works.

---

### Post by Ludwik on 2006-10-28
> **mykmelez said:**
> 
640x480/vga=785
800x600/vga=788
1024x768/vga=791
1280x1024/vga=794


Still doesn't work. 785 acts differently than others, because it doesn't show the message about undefined mode number, but the screen is completely black during whole boot process.

---

### Post by mongee on 2006-10-28
I am having the same problems that ludwik is having, everytime I add a vga= into the menu.lst file I get "undefined mode number" error. I tried all of the modes listed on [this thread]("http://www.ubuntuforums.org/showthread.php?p=1541970")
At the moment, so that I can at least see whats happening, I have removed the "quiet" and "splash" references from the menu.lst file so that I can at least see whats happening on startup. It would be nice to be able to see a splash screen though :)

---

### Post by Ludwik on 2006-10-28
> **mongee said:**
> It would be nice to be able to see a splash screen though :)

Yeah. And when Ubuntu really can't display splash screen it should automatically switch to traditional text-based booting messages. When I booted Edgy after upgrade and it was showing just blank screen I thought that my system is completely broken, so I installed it from scratch... just to experience the same problem. Any messages would show me that something is going on, and my system isn't dead.

---

### Post by ZagiFlyer on 2006-10-28
> **Midway said:**
> 

. . .

**Searching for splash image ... none found, skipping ...**

. . .



I think you may be onto something here - that's the same result I get. Does this also apply to the shutdown screen? I don't see that either.

---

