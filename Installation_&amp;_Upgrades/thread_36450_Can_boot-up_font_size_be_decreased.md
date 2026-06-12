---
title: "Can boot-up font size be decreased?"
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by jonrkc on 2005-05-23
The messages at Ubuntu Hoary boot time are displayed in a large font.  Booting with either Mandriva Linux or Knoppix Live CD displays messages in a much smaller and easier-to-read font.

Is there a way to change font size at boot time?  Or is it determined within the kernel?

---

### Post by tread on 2005-05-23
Its a framebuffer option.
You can set it with vga=something in the boot options in grubs menu.lst file, else set vga=ask which will prompt you for the resolution.

But I'd suggest hunting around for the font size you want, cos vga=ask always seem to show very limited options (at least for me)

---

### Post by jonrkc on 2005-05-23
[QUOTE=tread]Its a framebuffer option.
You can set it with vga=something in the boot options in grubs menu.lst file, else set vga=ask which will prompt you for the resolution.

But I'd suggest hunting around for the font size you want, cos vga=ask always seem to show very limited options (at least for me)[/QUOTE]
 Hey, thanks very much!  I should be able to get it more readable now.  I searched for a half hour on Google without finding this answer.  Thanks again.

---

### Post by hyperboloid on 2005-06-02
[QUOTE=jonrkc]The messages at Ubuntu Hoary boot time are displayed in a large font.  Booting with either Mandriva Linux or Knoppix Live CD displays messages in a much smaller and easier-to-read font.

Is there a way to change font size at boot time?  Or is it determined within the kernel?[/QUOTE]

Very simple. 

1. Using your favorite editor, find the line that begins
```
# kopt=root=/dev/hda1 ro 
``` in the file /boot/grub/menu.lst and append the string "vga=0x318" to the end of that line. Do not uncomment! The line in my file looks like this: ```
# kopt=root=/dev/hda1 ro vga=0x318
``` [Replace 0x318 with a sizing entry adapted to your system; this one works well for me.]

2. Save the file and run the command:```
$ sudo update-grub
```

3. Reboot.

---

### Post by mingus on 2005-06-02
Before placing the vga= argument in menu.lst . . .

Googling can quickly get you a table of video resolution values.  It can be expressed as an integer or hexidecimal (the preceding 0x).  The value also specifies the color depth.  It is important that this be matched up with your video card and monitor.  For example, 0x317 is 1024x768@24bit.  If you use a value beyond what your card can handle, you'll have a problem (in the case of older laptops, you can fry the display).

---

### Post by jonrkc on 2005-06-02
[QUOTE=mingus]Before placing the vga= argument in menu.lst . . .

Googling can quickly get you a table of video resolution values.  It can be expressed as an integer or hexidecimal (the preceding 0x).  The value also specifies the color depth.  It is important that this be matched up with your video card and monitor.  For example, 0x317 is 1024x768@24bit.  If you use a value beyond what your card can handle, you'll have a problem (in the case of older laptops, you can fry the display).[/QUOTE]
 Thanks to both mingus and hyperboloid for the useful tips!  I couldn't find a chart of video resolution values via Google, but I examined the boot configuration on my Knoppix disk, as Knoppix has a beautiful boot-up appearance (as distinguished from the appearance once it's working under X, which is LOUSY on my machine).  I found the value vga=791 and applied that to my file and did update-grub, rebooted, and now I have antialiased characters in the proper size for my display, just as with Mandrake/Mandriva or Knoppix (only Knoppix has all those pretty colors, too).  

Not only that, but the setting persists into the terminal, so that when I go to terminal 1 as I frequently do, I now no longer have to put up with what looks like an 800x600 display on my 1280x1024 terminal, but have much more readable text.  Midnight Commander is still messed up in several ways, with extraneous characters, blank areas, etc., but at least it's a lot more readable and I can read both columns now. 

Thanks again--this is a big improvement for my day-to-day working.

---

### Post by 23meg on 2005-06-02
[here](http://linuxbasics.org/Members/SRM/Published/vga_set/view) is the table. i haven't found a copy of it that includes modes for 1400x1050 though; perhaps it's not supported?

---

### Post by tethys on 2008-05-22
i know this is frickin old, but i need a mode for 1280x800, I type the ol sudo hwinfo --framebuffer, but the screen doesnt stay long enough for me to look for it

---

