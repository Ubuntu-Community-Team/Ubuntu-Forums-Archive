---
title: "My opinion on the beta, and what should be improved"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gjoellee on 2010-03-19
I am amazed of how well the beta is, there is however some things I think should be improved.

1. The metacity buttons order, should be changed as they are moved to the left (which is nice, because I don't have to move my cursor across the screen to click at "Files" in example), but the current order of the buttons are the same as they are if they would have been put on the right side.

Current order of he buttons: Maximize --> Minimize --> Close
It should be: Close --> Minimize --> Maximize


2. To get the best boot experience GRUB should be themed, or maybe we should consider using "BURG" (but as we this release is in a Beta, that might not happen)

3. It is heard reading the text in the selected window in the panel window lists:
[[IMG]http://img100.imageshack.us/img100/8945/screenshotxt.png[/IMG]]("http://img100.imageshack.us/i/screenshotxt.png/")

4. I think the fonts are too big...it looks better with size 9 instead of 10

5.  For some reason cooling fans in my laptop seams to be running at full all the time. It does not do that in windows. WHY?

6. The links in the dropdown list here is hard to read:
 [[IMG]http://img291.imageshack.us/img291/6320/screenshotinterfacelift.th.png[/IMG]]("http://img291.imageshack.us/i/screenshotinterfacelift.png/")

7. I might add more things here if I find any

---

### Post by grubdude on 2010-03-19
They also need to get it to work with Virtualbox Guest Additions. I am only able to use low screen resolution since kernel -15. After -16 was released it no longer works...
 
I will continue to just run my -15 kernel and update my build, for now.

---

### Post by dyltman on 2010-03-19
1-4 has been said before.

---

### Post by katie-xx on 2010-03-19
I really do like the way you have put that post together. Its precise and accurate and conveys exactly what you meant to say without waffling on and on. Super stuff :)

Apart from that the reason Ive answered is to say I havent had any difficulty with cooling fans running on my machine so perhaps it might be a good idea to take a closer look at what was happening in your box.

(hey ..I love your doggy avatar as well :)

Kate

---

### Post by spyderpride on 2010-03-19
> **gjoellee said:**
> I am amazed of how well the beta is, there is however some things I think should be improved.

1. The metacity buttons order, should be changed as they are moved to the left (which is nice, because I don't have to move my cursor across the screen to click at "Files" in example), but the current order of the buttons are the same as they are if they would have been put on the right side.

Current order: Maximize --> Minimize --> Close
It should be: Close --> Minimize --> Maximize

[COLOR="Navy"]You can do this yourself in gconf-editor (command line or alt+F2 works). I believe it is in apps-->metacity-->general. The default is something like 'maximize,minimize,close:menu'.  Change the order of that to get what you want.[/COLOR]

2. To get the best boot experience GRUB should be themed, or maybe we should consider using "BURG" (but as we this release is in a Beta, that might not happen)

[COLOR="Navy"]Ditto... ditto.[/COLOR]

3. It is hard reading the text in the selected window in the panel window lists:
[[IMG]http://img100.imageshack.us/img100/8945/screenshotxt.png[/IMG]](http://img100.imageshack.us/i/screenshotxt.png/)


4. I think the fonts are too big...it looks better with size 9 instead of 10

[COLOR="Navy"]System-->Prefs-->Appearance-->Fonts.  I normally switch all mine to 9 anyway, just looks better.[/COLOR]

5.  For some reason cooling fans in my laptop seams to be running at full all the time. It does not do that in windows. WHY?

[COLOR="Navy"]This is a difficult issue as it probably has to do with very low-level settings (acpi modules).  What is the make and model of your laptop? Has the fan always ran a lot more in Ubuntu than it does in Windows?[/COLOR]

6. I might add more things here if I find any

.

---

### Post by sdowney717 on 2010-03-19
> 1. The metacity buttons order, should be changed as they are moved to the left (which is nice, because I don't have to move my cursor across the screen to click at "Files" in example), but the current order of the buttons are the same as they are if they would have been put on the right side.

Current order: Maximize --> Minimize --> Close
It should be: Close --> Minimize --> Maximize

you can edit this and make it any order you want and on either the left or right

[http://ubuntuforums.org/showthread.php?p=8959917#post8959917](http://ubuntuforums.org/showthread.php?p=8959917#post8959917)

---

### Post by gjoellee on 2010-03-19
> **spyderpride said:**
> .
  See my signature

---

### Post by gjoellee on 2010-03-19
> **katie-xx said:**
> I really do like the way you have put that post together. Its precise and accurate and conveys exactly what you meant to say without waffling on and on. Super stuff :)

Apart from that the reason Ive answered is to say I havent had any difficulty with cooling fans running on my machine so perhaps it might be a good idea to take a closer look at what was happening in your box.

(hey ..I love your doggy avatar as well :)

Kate

Thank you, I am really interested in having easy-to-read post. (and that is my dog actually)

> **sdowney717 said:**
> you can edit this and make it any order you want and on either the left or right

[http://ubuntuforums.org/showthread.php?p=8959917#post8959917](http://ubuntuforums.org/showthread.php?p=8959917#post8959917)

It messes up the button background. Just looks weird.

---

### Post by spyderpride on 2010-03-19
EDIT: imo the new Light themes seem kind of half-baked.  The styling is nice, but they really lack functionality.  Key issues being the window list colors on Ambiance and the window buttons on both.  I have always used DarkRoom, and I will continue to do so.

For your heat issue... a quick google told me that the fglrx video driver may help.  Not positive it will, or if it is even possible to use in 10.04 right now.

---

### Post by grubdude on 2010-03-19
Woof! :-)

---

### Post by leandromartinez98 on 2010-03-19
The issue with the fonts you should report as a bug. This is something they are able to solve until release, and I think it is important for the consistency of the new themes.

---

### Post by keybuk on 2010-03-19
> **gjoellee said:**
> 2. To get the best boot experience GRUB should be themed, or maybe we should consider using "BURG" (but as we this release is in a Beta, that might not happen)

The reason we don't theme GRUB is because there's no way to natively program an accelerated graphics mode from a tiny tiny boot loader.

Since we can't do that, if we do do pretty graphics, it's in a VESA mode like 1024x768x8bpp.  That looks pretty crud on a widescreen panel - but it's also not the mode that the X server will run in - so you get a horrid monitor switch off/on modeswitch (two actually).

Paradoxically it's therefore a better "experience" to not theme it.

---

### Post by dcstar on 2010-03-19
> **keybuk said:**
> The reason we don't theme GRUB is because there's no way to natively program an accelerated graphics mode from a tiny tiny boot loader.

Since we can't do that, if we do do pretty graphics, it's in a VESA mode like 1024x768x8bpp.  That looks pretty crud on a widescreen panel - but it's also not the mode that the X server will run in - so you get a horrid monitor switch off/on modeswitch (two actually).

Paradoxically it's therefore a better "experience" to not theme it.

It's almost getting to the stage where keeping backwards compatibility for a boot loader is almost not worth the effort.

People these days equate their modern PC experience with fancy boot-up screens and no cludgy old text stuff that dates back to the 1980's.

As long as Linux remains true to its technical roots by keeping compatibility and using VESA text screens, it will look second-rate compared to the OSs that just show fancy high-def graphics from the start.

---

### Post by SaintStewart on 2010-03-19
> **gjoellee said:**
> 5.  For some reason cooling fans in my laptop seams to be running at full all the time. It does not do that in windows. WHY?


^


This.  



In addition to having a slew of other problems, my lappy has been running hotter with the fan near constant on since I have installed the beta.

---

### Post by keybuk on 2010-03-19
> **dcstar said:**
> It's almost getting to the stage where keeping backwards compatibility for a boot loader is almost not worth the effort.

People these days equate their modern PC experience with fancy boot-up screens and no cludgy old text stuff that dates back to the 1980's.

As long as Linux remains true to its technical roots by keeping compatibility and using VESA text screens, it will look second-rate compared to the OSs that just show fancy high-def graphics from the start.

It's nothing to do with compatibility actually; it's just impossible to do.

And it's worth pointing out that no other OS has fancy high-def graphics for its boot loader.  Linux is unusual in that you tend to see the boat loader, because you use it to dual boot.

---

### Post by dcstar on 2010-03-19
> **keybuk said:**
> It's nothing to do with compatibility actually; it's just impossible to do.

And it's worth pointing out that no other OS has fancy high-def graphics for its boot loader.  Linux is unusual in that you tend to see the boat loader, because you use it to dual boot.

You've just highlighted the problem - and the mindset - that causes it.

Linux **is** unusual because it does offer a nice tech-savvy boot loader option, and that scares the crap out of a lot of people who are not used to that sort of thing because their usual OS boots straight into a nice full GUI experience.

It doesn't have to be so, the 10.04 boot ISOs present a nice graphical screen asking you to choose a region and then either test or install Ubuntu - that is the sort of menu system *normal* people expect these days.

Yes, something that presents a GUI boot list will be slower than a basic text based menu like Grub, but as long as Linux uses that sort of legacy thing it will be perceived as something strange by the majority of non-tech heads.

---

### Post by keybuk on 2010-03-19
> **dcstar said:**
> It doesn't have to be so, the 10.04 boot ISOs present a nice graphical screen asking you to choose a region and then either test or install Ubuntu - that is the sort of menu system *normal* people expect these days.

Yes, something that presents a GUI boot list will be slower than a basic text based menu like Grub, but as long as Linux uses that sort of legacy thing it will be perceived as something strange by the majority of non-tech heads.

Sure, but that's not the boot loader ;-)

As you've already just pointed out - we're working on exactly this problem already!

---

### Post by descendent87 on 2010-03-19
Some good points, I agree with 3, 4 (although I prefer size 8, this may be too small for some people) and 6.
The window buttons are fine the way they are in my opinion, takes a bit of getting used to but then it seems normal.
Also I feel that with the new themes they should have ditched the brown more than they have and gone with more purple/aubergine (whatever you want to call it). Especially for things like active windows on the panel (screenshot for point 3)

---

### Post by gjoellee on 2010-03-20
> **descendent87 said:**
> Some good points, I agree with 3, 4 (although I prefer size 8, this may be too small for some people) and 6.
The window buttons are fine the way they are in my opinion, takes a bit of getting used to but then it seems normal.
Also I feel that with the new themes they should have ditched the brown more than they have and gone with more purple/aubergine (whatever you want to call it). Especially for things like active windows on the panel (screenshot for point 3)

I agree....I am using size 8 on all fonts now. It looks way better!

---

### Post by descendent87 on 2010-03-20
I also switch the font to droid sans (in the repos) as I prefer it

---

### Post by lavinog on 2010-03-20
> **dcstar said:**
> 
Linux **is** unusual because it does offer a nice tech-savvy boot loader option, and that scares the crap out of a lot of people who are not used to that sort of thing because their usual OS boots straight into a nice full GUI experience.

It doesn't have to be so, the 10.04 boot ISOs present a nice graphical screen asking you to choose a region and then either test or install Ubuntu - that is the sort of menu system *normal* people expect these days.


Remove windows and you can get the nice graphical boot that you desire.
If you are not dual booting, you don't need to see the grub menu at all.

The problem with your solution is that I would have to boot into a gui menu, select my os which will cause the system to reboot into that os.  It takes my system almost 10 seconds to even get to the grub menu...This would add an additional 10 seconds because of the reboot.

---

