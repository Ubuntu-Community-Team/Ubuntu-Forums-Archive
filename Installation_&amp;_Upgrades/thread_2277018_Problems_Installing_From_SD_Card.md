---
title: "Problems Installing From SD Card"
date: 2015-05-06
forum: Installation &amp; Upgrades
---

### Post by typos1 on 2015-05-06
I ve installed ubuntu from CD many times before, but never from USB or SD. 

I m trying to install from SD card on a computer without a CD drive. After turning on I go the usual prompt asking whether I want to try ubuntu or install it, I clicked install then I got a screen asking about wifi, then it froze and the mouse didnt work. 

I left it for 15 mins it was still frozen. 

So I rebooted and now I just get the ubuntu wallpaper, no prompts or anything. 

I ve left it for as long as half an hour and its still the same. 

I ve also tried a USB drive and still, all I get is the ubuntu wallpaper no prompts or anything. 

I ve tried this multiple times.

No really sure what to do now :-/

---

### Post by RobGoss on 2015-05-06
I think installing Ubuntu from a DVD Or USB, would be much easier it's a simple process and only takes a few minutes.

---

### Post by typos1 on 2015-05-06
There is no disc drive on it !

I chose SD card over USB because its faster.

But I ve tried it with both USB and SD card now and it just hangs on the wallpaper, no prompts at all.

---

### Post by sudodus on 2015-05-06
I guess it is not the computer in your signature. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes is possible to give better advice. Otherwise we can only guess what is your problem (for example that it is a netbook with too little horsepower or RAM for standard Ubuntu, but it might be a completely different problem, for example the graphics driver).

---

### Post by typos1 on 2015-05-06
Yeah, soz, fair enough, but I m thinking that the problem is cos it started to write stuff to the hard drive or something. 

Its an A6 3420M processor/onboard graphics on a Sabine A2 minibox board, with 8Gb RAM, cant remember the wifi chip at the moment.

---

### Post by sudodus on 2015-05-06
I suspect that you have problems with the graphics driver or wifi driver (if there is a wifi chip).

It seems to be AMD graphics (AMD Radeon HD 6520G according to [this link]("http://www.notebookcheck.net/AMD-A-Series-A6-3420M-Notebook-Processor.61302.0.html")) , and the built in driver might not work well. Try to boot with the boot option **nomodeset** or **text**. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)[URL="https://help.ubuntu.com/community/BootOptions"]
[/URL]

***Edit***: I should add that I have very little experience of AMD/ATI/Radeon graphics, so I welcome other people to chip in and help.

---

### Post by typos1 on 2015-05-06
Thanks, that seems to have helped, I m getting somewhere now. 

I do remember reading there maybe a problem with the graphics, but I m sure I also read that there was a solution.

---

### Post by sudodus on 2015-05-06
If you know how to get AMD Radeon HD 6520G (or a similar graphics chip) to work well, please chip in an help!

No pun intended ;-)

---

### Post by typos1 on 2015-05-06
Ah, no I dont, I just remember reading about a problem someone had and that they got it sorted, hence why I bought this new pc.

Your reply makes me think I messed up and there is still a problem and fills me with trepidation :-/

I was gonna stick with on board graphics as I dont really do gaming and I ve read that its fine for video, looks like I may have to shell out for a graphics card.

---

### Post by sudodus on 2015-05-06
A misunderstanding: I thought 'getting somewhere' meant that the graphics is working, but not well enough. If you are happy with it, I don't want you to think you have messed up. Please stay happy :-)

---

### Post by typos1 on 2015-05-06
Yeah, its all installed now - thats what I meant by "getting  somewhere", but screen res is totally wrong - too small and wrong aspect ratio, no other options in "displays", trying propretory drivers now, first one no change.

When you said "If you know how to get AMD Radeon HD 6520G (or a similar graphics chip) to work well, please chip in an help!" it suggested to me that the 6520G doesnt work and its a known problem, which is why I think I ve messed up.

---

### Post by typos1 on 2015-05-06
Looks like you were spot on with why it wasnt working when I tried to install it - just installed first prop driver option and after booting and logging in I get the ubuntu wallpaper onscreen and nothing else just like I when I was trying to install it.

Any ideas how I go back to the previous driver ? Safe mode or one of the options at first boot ?

---

### Post by typos1 on 2015-05-06
Actually scrap that, it seems to be fine now apart from the screen - the display is zoomed so I cant actually see the icons in unity, but they are actually there because a menu appears when I put the mouse at the side of the screen. 

I ve temporarily switched to a lower res so I can see unity. 

My display is shown as 46" in ubuntu but its actually 26", ubuntu says the same thing on my old pc, but it displays correctly without zooming in so I can see unity.

---

### Post by sudodus on 2015-05-06
What resolution gives you a working screen? It might be possible to use xrandr (command line) or arandr (GUI) to set the screen so that it works. I know it is possible, but I am not good at using it (so not good at helping). But it is a tip, you might find something about it via the internet or maybe here at the Ubuntu Forums.

It might be a good idea to finish this thread, and start a new one with a good title about screen resolution.

---

### Post by typos1 on 2015-05-06
Actually, having thought about it, I dont think I ever had problems installing after all - I think it installed fine, but because of the way it was displayed on the screen cutting off unity and the top bar, I thought it had hung installing !!

They all work - even the one where I cant see unity works cos the menus appear when I mouse near them, its just I want it to fit the screen correctly, I ll try the other drivers, googling, xrandr (which I think I ve used before) and another section of this forum.

I ll mark it as solved and thanks for your help ! :-)

---

### Post by sudodus on 2015-05-06
You are welcome and good luck with the graphics / screen resolution :-)

---

### Post by typos1 on 2015-05-10
I m now having problems with the screen resolution and the proprietary Radeon drivers, the picture is appalling with the proprietary driver and the the open source one only gives one resolution which is an incorrect one. Lots of searching has found similar problems caused by nomodeset and as in the end I dont think I actually needed to change to nomodeset the picture was just zoomed in slightly, I think its nomodeset that is causing the display problems. Can you tell me how to change it back to the default ? Thanks

---

### Post by sudodus on 2015-05-10
Edit the file **/etc/default/grub**,

```
sudo nano /etc/default/grub
```

and change one of the lines that starts with

```

GRUB_CMDLINE_LINUX_DEFAULT=
or
GRUB_CMDLINE_LINUX=

```

and contains the word **nomodeset** - remove that word, save the file, and run the command

```
sudo update-grub
```

After that the system should boot without the boot option nomodeset.

---

### Post by typos1 on 2015-05-10
Thanks.

So I leave the "GRUB_CMDLINE_LINUX=" bit and just remove "nomodeset" ?

Feel a bit stupid here, but I cant edit it, it wont let me delete and I really dont understand the controls at the bottom of the terminal - I ve tried pressing " ^ " and whatever other key it says but nothing happens.

---

### Post by sudodus on 2015-05-11
> **typos1 said:**
> Thanks.

So I leave the "GRUB_CMDLINE_LINUX=" bit and just remove "nomodeset" ?
Yes> 
Feel a bit stupid here, but I cant edit it, it wont let me delete and I really dont understand the controls at the bottom of the terminal - I ve tried pressing " ^ " and whatever other key it says but nothing happens.

In nano: move the cursor (the current position) with the arrow keys (up, down, left, right), and use the delete key to delete a character.

Use the hotkey combination ***ctrl x*** to exit (in this case ^ means the control key) - and you will be asked if you want to save the modified buffer. Answer Y (yes) and confirm writing to the file (with the Enter key).

---

### Post by typos1 on 2015-05-11
Thanks :-)

---

