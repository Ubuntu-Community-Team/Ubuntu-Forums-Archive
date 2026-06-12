---
title: "05_debian-theme doesn't seem to work now."
date: 2010-01-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2010-01-12
The installs I have updated and the A2 I installed all seem to have lost the ability to throw up a background.

---

### Post by phillw on 2010-01-12
<< vomits over RH's computer for him ;)

In the UK "Throw Up" == Vomit :lolflag:

I've not even got as far as playing with pretty boot screens, but there is an awesome background picture programme, if you like astronomy - of some spectacular shots of planets, universes etc.  [http://sanchezluis.blogspot.com/2010/01/create-wallpaper-slideshow-in-ubuntu.html](http://sanchezluis.blogspot.com/2010/01/create-wallpaper-slideshow-in-ubuntu.html)

Or, for another look at it --> [http://ubuntuforums.org/archive/index.php/t-459912.html](http://ubuntuforums.org/archive/index.php/t-459912.html)

I may have a play with putting it on a cron job, the images are truly breathtaking !!!

Regards,

Phill.

---

### Post by ranch hand on 2010-01-12
I like the looks of those.

The background I am not getting up, though, is in grub1.98.  The /etc/grub.d/05_debian-theme file, when edited, should put your properly sized image up behind your screen menu.  Been doing this since back in Kinky Kitty testing (9.10 is Kinky Kitty just as 10.04 is Lounge Lizard).

Now all I am getting is the default black background.  This does not bother me much as I only see it for a few seconds but it is nice if that background comes up as your gdm login background and then your wallpaper.

It also acts, for me, as an indicator of which Lizard is boot/root at the moment.

Edit;
Did not look at the forums post you linked before writing the above.  zombie robot is one of the artists for Stoner Edition (Ubuntu respin - I like it).  He has a neat background for it that is all based on the same central image and fades from one to the next.

---

### Post by caryb on 2010-01-12
I had the need to use single user mode last night & to my shock esc wont break out to a menu any more. I had to guess what was on the screen (was all gibberish) to do a apt-get update/upgrade etc to fix the problem. So what I'm saying is that grub is buggered at the moment.


Cary


BTW to add another word for vomit in Australian slang we say chunder :lolflag:

---

### Post by tad1073 on 2010-01-12
here is my 05_debian-theme file
[http://pastebin.ca/1749043](http://pastebin.ca/1749043)

bg images work fine here

---

### Post by ranch hand on 2010-01-12
> **tad1073 said:**
> here is my 05_debian-theme file
[http://pastebin.ca/1749043](http://pastebin.ca/1749043)

bg images work fine here
I see that you are using a .tga image.  I am using .png.  I wonder if that is the problem.  It should not be but that may be it.

I will try that in the morning.  I am on my main drive for the night.  I use a Lizard (10.04 as we all know is Lounge Lizard) as my production OS in the daytime when I can watch it pretty regularly.  At night I have a 9.04 respin running.  I have boinc on both of them and set to crank the cpu at pretty much 100% so I want one that I KNOW is stable running when I am asleep.

Other than the .tga your file is pretty much like all of mine.  I do change the text color to make sure I can read the menu over the bg but that should not be a problem and I have a couple of installs where the image is compatible with the default.

I will change that back to the white/black - black/white anyway just to be sure.

Thanks, you may have pointed me in the right direction.  I can edit the images from here tonight.  Can't update grub from here as that is against my rules.  This drive does not get involved in operations like that.  I will work through nautilus but that is the limit.

---

### Post by ranch hand on 2010-01-13
I changed the stuff around and tried to update grub and got an error about "unexpected end of file line 62".  I found this interesting in a 61 line file.

Tried a different install.  Same deal.  Tried a third install and it worked fine.  I am in it now and changed it back to a .png and one color change and will try it again.  If it works I will transplant it to the others as they must, in some way,  be corrupt although I can't find any differences.

---

### Post by ccw on 2010-01-13
> **phillw said:**
> << vomits over RH's computer for him ;)

In the UK "Throw Up" == Vomit :lolflag:

Yeah, it could mean that here in the US too.

---

### Post by drs305 on 2010-01-13
ranch hand,

I just changed from VM to a hard drive install of A2. The debian theme .png image worked fine for me.

---

### Post by ranch hand on 2010-01-13
It is working fine for me too.  I do not quite understand where the problem was as all the files were alike but 2 of my installs did not work.

Replacing the /etc/grub.d/05_debian-theme file with one from another install worked and is working fine with the .png file.

I can also change the font color.

Everything is cool now but it had me going for a while.

---

