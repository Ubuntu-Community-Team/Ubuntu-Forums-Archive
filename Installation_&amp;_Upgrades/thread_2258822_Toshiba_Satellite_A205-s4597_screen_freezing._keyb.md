---
title: "Toshiba Satellite A205-s4597 screen freezing. keyboard dies"
date: 2014-12-30
forum: Installation &amp; Upgrades
---

### Post by Harold_1556 on 2014-12-30
I have a Toshiba Satellite A205-s4597 I installed Ubuntu on it a few years ago. It's updated to the most recent version of 14 LTS. I use it mainly for word processing and web surfing. 

About three months ago there was a big update, or at least it seemed big to me at the time. Ever since then I've been experiencing freezes on start up, issues with the keyboard, Open Office greying out while trying to load a 500k text file and now freezes while running and on shut down. The keyboard problem is that, every once in a while, the keyboard will either stop working or not respond correctly on key press. Either the keys won't do what they're supposed to, arrow keys won't move the cursor correctly, it'll hop around skipping words, or letter keys will type a different letter than it's supposed to or nothing at all. Yet the mouse still works and I can save and close the program. The keyboard issue is very infrequent and usually fixed by restarting.

The freezes are a problem though. I thought maybe one of the updates just didn't install correctly. I was going to burn a new install disk, with hopefully the latest updates, and format my drive and reinstall fresh. When I went to the Ubuntu download page I see there is a 32 bit version.

My Satellite is a 32 bit Vista machine with 2gigs of Ram. It's a Intel Centrino duo processor that I think is 800 Mghz, with 160 gig HD.

So my question is, do I install the 64 bit Ubuntu, the 32 bit or is there another solution I'm missing? I was toying with XUbuntu. That's supposed to be a "lighter" version of the OS. Would that be better for this machine?

---

### Post by sammiev on 2014-12-30
I would try both live from a USB/DVD and see what works best for you. You may just had a bad update and a fresh install may do the trick. GL :P

---

### Post by grahammechanical on 2014-12-30
> [COLOR=#000000]So my question is, do I install the 64 bit Ubuntu, the 32 bit or is there another solution I'm missing? [/COLOR]

We cannot run a 64 bit OS on a 32 bit CPU.

> [COLOR=#000000]My Satellite is a 32 bit Vista machine with 2gigs of Ram. It's a Intel Centrino duo processor that I think is 800 Mghz, with 160 gig HD.[/COLOR]

We need to separate freezes of the OS with freezes in OpenOffice. Or is that LibreOffice? Have you installed OpenOffice? I ask because LibreOffice has been the default in Ubuntu for some years.

When LibreOffice greys out like that it is an indication that the application is busy. When I have two large Writer documents open at the same time and set them to save at the same time I get the same effects as you. It is not the operating system that is freezing.

I do not think that you are correct about the CPU speed. 

[http://www.cnet.com/products/toshiba-satellite-a205-s4597-core-duo-1-86ghz-2gb-ram-160gb-hdd-vista-home-premium/specs/](http://www.cnet.com/products/toshiba-satellite-a205-s4597-core-duo-1-86ghz-2gb-ram-160gb-hdd-vista-home-premium/specs/)

According to that link it is an Intel Core Duo T2350 / 1.86GHZ. Where the difficulty lies, I think is with the video adapter. It is Intel GMA 950 with maximum allocated RAM size of 256MB. And it is that video memory size that I would say is border-line for running Ubuntu + Unity 3D. You might even be running with the fall back open source video driver called llvmpipe that is used when the graphic adapter cannot support Unity 3D. 

You can run  this command

```
/usr/lib/nux/unity_support_test -p
```

You should see something like this

> /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.3.2


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes


If you do not then your graphic adapter is unsuitable for Unity 3D.

Regards.

---

### Post by sammiev on 2014-12-30
The above poster seen something I missed and that is your system is only 32bit.

---

### Post by lisati on 2014-12-30
*cough* 
I might have missed something, but.....

I have a Toshiba Satellite with similar specs, one from the M200 product range and which came with Vista preinstalled. Although I'm currently running 32-bit 12.04, its processor (also an Intel Centrino, a T5450) can apparently cope with a 64-bit OS.

---

### Post by Bucky Ball on 2014-12-30
Welcome. I have changed the title of your thread in the hopes it may garner further support. You improve your chance of support with titles describing your issue. Generic titles don't give potential helpers much info. 

Good luck. ;)

---

### Post by Harold_1556 on 2014-12-30
@grahammechanical Sorry, you're right, it's Libra Office. it doesn't freeze in Office though. It does gray out when loading a file and when I do have the keyboard issue it's in Office.

I have to admit I'm not sure about the specs of the machine. It was given to me 5 years ago. I did a search and found a terminal command to get the computer specs. I find it a little confusing to read. Looking at it again I see this line:

Intel(R) Core(TM) Duo CPU T2350 @ 1.86GHz

So yeah, you're right about that too :-) I tried running the support test you gave me:
/usr/lib/nux/unity_support_test -p

I'm not very experienced in Linux. I was able to cd from usr to lib but was told there was no nux dir. However the mySpecs.html has this section:

[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"]display:0
[/TD]
[/TR]
                [TR]
[TD="class: first"]description: [/TD]
[TD="class: second"]VGA compatible controller[/TD]
[/TR]
              [TR]
[TD="class: first"]product: [/TD]
[TD="class: second"]Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller[/TD]
[/TR]
              [TR]
[TD="class: first"]vendor: [/TD]
[TD="class: second"]Intel Corporation[/TD]
[/TR]
              [TR]
[TD="class: first"]physical id: [/TD]
[TD="class: second"]2
[/TD]
[/TR]
              [TR]
[TD="class: first"]bus info: [/TD]
[TD="class: second"]pci@0000:00:02.0
[/TD]
[/TR]
              [TR]
[TD="class: first"]version: [/TD]
[TD="class: second"]03[/TD]
[/TR]
              [TR]
[TD="class: first"]width: [/TD]
[TD="class: second"]32 bits[/TD]
[/TR]
              [TR]
[TD="class: first"]clock: [/TD]
[TD="class: second"]33MHz[/TD]
[/TR]
              [TR]
[TD="class: first"]capabilities: [/TD]
[TD="class: second"]msi pm vga_controller bus_master cap_list rom [/TD]
[/TR]
              [TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] driver[/TD]
[TD]=[/TD]
[TD]i915[/TD]
[/TR]
[TR]
[TD="class: sub-first"] latency[/TD]
[TD]=[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
              [TR]
[TD="class: first"]resources:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] irq[/TD]
[TD]:[/TD]
[TD]16[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]f0a00000-f0a7ffff[/TD]
[/TR]
[TR]
[TD="class: sub-first"] ioport[/TD]
[TD]:[/TD]
[TD]1800(size=8)[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]d0000000-dfffffff[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]f0b00000-f0b3ffff[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]


And this section too (and it's in red in the report too):


[TABLE="class: node-unclaimed, width: 100%"]
[TR]
[TD="class: first"][COLOR=#ff0000]id:
[/COLOR][/TD]
[TD="class: second"][COLOR=#ff0000]display:1[/COLOR]
[/TD]
[/TR]
                [TR]
[TD="class: first"][COLOR=#ff0000]description: [/COLOR][/TD]
[TD="class: second"][COLOR=#ff0000]Display controller[/COLOR][/TD]
[/TR]
              [TR]
[TD="class: first"][COLOR=#ff0000]product: [/COLOR][/TD]
[TD="class: second"][COLOR=#ff0000]Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller[/COLOR][/TD]
[/TR]
              [TR]
[TD="class: first"][COLOR=#ff0000]vendor: [/COLOR][/TD]
[TD="class: second"][COLOR=#ff0000]Intel Corporation[/COLOR][/TD]
[/TR]
              [TR]
[TD="class: first"][COLOR=#ff0000]physical id: [/COLOR][/TD]
[TD="class: second"][COLOR=#ff0000]2.1[/COLOR]
[/TD]
[/TR]
              [TR]
[TD="class: first"][COLOR=#ff0000]bus info: [/COLOR][/TD]
[TD="class: second"][COLOR=#ff0000]pci@0000:00:02.1[/COLOR]
[/TD]
[/TR]
              [TR]
[TD="class: first"][COLOR=#ff0000]version: [/COLOR][/TD]
[TD="class: second"][COLOR=#ff0000]03[/COLOR][/TD]
[/TR]
              [TR]
[TD="class: first"][COLOR=#ff0000]width: [/COLOR][/TD]
[TD="class: second"][COLOR=#ff0000]32 bits[/COLOR][/TD]
[/TR]
              [TR]
[TD="class: first"][COLOR=#ff0000]clock: [/COLOR][/TD]
[TD="class: second"][COLOR=#ff0000]33MHz[/COLOR][/TD]
[/TR]
              [TR]
[TD="class: first"][COLOR=#ff0000]capabilities: [/COLOR][/TD]
[TD="class: second"][COLOR=#ff0000]pm bus_master cap_list [/COLOR][/TD]
[/TR]
              [TR]
[TD="class: first"][COLOR=#ff0000]configuration:[/COLOR][/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"][COLOR=#ff0000] latency[/COLOR][/TD]
[TD][COLOR=#ff0000]=[/COLOR][/TD]
[TD][COLOR=#ff0000]0[/COLOR][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
              [TR]
[TD="class: first"][COLOR=#ff0000]resources:[/COLOR][/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"][COLOR=#ff0000] memory[/COLOR][/TD]
[TD][COLOR=#ff0000]:[/COLOR][/TD]
[TD][COLOR=#ff0000]f0a80000-f0afffff
[/COLOR][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]


Honestly I don't remember a choice when I first installed Ubuntu. Where/how would I be able to what bit version I have installed?

---

### Post by lisati on 2014-12-30
Thanks for the update with the specs.......and the reminder that not all Toshiba Satellites are equal......

/me hides in shame..... ):P

You'll need the 32-bit OS.

---

### Post by Bucky Ball on 2014-12-30
Yep, you want the 32bit version of Ubuntu. For a complete run down from the terminal, you can try:

```
lspci
```

That will give you all hardware specs. ;)

---

### Post by Harold_1556 on 2014-12-30
Thanks Bucy Ball for changing the title of the thread to something more appropriate. 

I forgot to mention that I found the mySpecs terminal command here in a forum search. I do have the entire HTML file but I didn't want to cut and paste the whole thing. If anyone wants to see the whole thing, or another section of it just let me know.

Thanks to all for your help.

---

### Post by Bucky Ball on 2014-12-30
You could copy and paste and use [code] tags to make it neat and small and easy to read. Check the last link in my signature to see how (I thing there are also [html] tags you can use, but haven't used them myself).

Use Adv Reply and you will find the # icon and possibly the option to enclose the output in [html] tags also.

---

### Post by Harold_1556 on 2015-01-01
Sigh, I went to backup everything worth saving onto a DVD before  reformatting and reinstalling Ubuntu and discovered my DVD drive is  dead. At first I thought the door was just stuck so I used the paperclip  trick. I got the door open but the drive doesn't spin and the light  doesn't come on. 

I've opened laptops in the past to do upgrades  or repairs I could look and see how much a new drive costs but I'm  wondering if it's just time to retire this machine.

 I saw something about installing Ubuntu from a USB stick. I have a 1 gig stick I could use. I'll have to look into that...

---

### Post by Bucky Ball on 2015-01-01
Not sure if 1Gb will be big enough. USB installs are common and UNetbootin is quite a popular way of creating the USB. Format the USB to FAT32 then burn the ISO to it using your USB burner of choice.

A DVD will hold about 4Gb? (Haven't used one for so long don't really know.) If that's the case, an 8/16/32Gb USB stick you can probably buy for under $20 (for 8Gb well under) and it has the advantage that it is reusable. Might be a better option than a new DVD drive. I bought a five pack of 8gb USB sticks about six months ago for less than $20. ;)

---

