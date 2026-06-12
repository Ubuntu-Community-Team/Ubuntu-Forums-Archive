---
title: "GRUB2 theming for lucid?"
date: 2010-01-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2010-01-03
I've come across the following cool stuff about GRUB2 theming:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

This just blew me away: [http://ubuntuguide.net/add-os-logos-into-grub2-boot-menu-using-burg](http://ubuntuguide.net/add-os-logos-into-grub2-boot-menu-using-burg) :guitar:

I tried using the themes without installing BURG but didnt seem to work so I guess its not merged back into upstream GRUB and I need to add the BURG repos.

I am currently trying out the ubuntu2 theme from [http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg](http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg) but this might also need BURG...

oh well, hoping for some nice boot loader eye candy for lucid - if not official then community based...

UPDATE: For latest install steps, please see: [http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)

---

### Post by dyltman on 2010-01-03
damn that'd be sweet

---

### Post by VMC on 2010-01-03
The first I head of BURG. Is this a one man show, or is there more dev's envolved?

 It looks nice and all, but I only spend 1 second looking at my grub2 menu screen , if that long.

---

### Post by SevenMachines on 2010-01-03
burg uses a modified version of [colin bennetts gfxmenu ]("http://grub.gibibit.com/About")code. the original code has been merged into [grub experimental]("http://bzr.savannah.gnu.org/r/grub/branches/experimental/") if any brave souls are looking to play with it. it needed a little work the last time i checked but did work ok. 
i believe there was a long thread on this during the karmic release (and also in arch) and a few of the screenshots made it onto the [grub2 community documentation]("https://help.ubuntu.com/community/Grub2")

---

### Post by SevenMachines on 2010-01-03
actually, i think the grub experimental branch (and so gfxmenu) is in [Felix Zielcke's PPA]("https://launchpad.net/%7Efzielcke/+archive/grub-ppa")

---

### Post by drs305 on 2010-01-03
> **SevenMachines said:**
> actually, i think the grub experimental branch (and so gfxmenu) is in [Felix Zielcke's PPA]("https://launchpad.net/%7Efzielcke/+archive/grub-ppa")

Yes it is. I was going to ask him the theming status but he's offline at the moment.

Update: This theme site may be better integrated into Ubuntu for the experimental branch of Grub - it's done by one of the Grub 2 devs who works with Ubuntu. Work still needs to be done on themes even here however:
[http://grub.gibibit.com/]("http://grub.gibibit.com/").

---

### Post by autocrosser on 2010-01-03
I've left E-mail messages with Bean & Felix about this thread---hope to have one of them drop by & talk about it---I've been waiting for this to get to a testing state for quite a while.....talked to the grub2 developer early in 2009 about it & it showed promise, so I've kept track of it......

---

### Post by BwackNinja on 2010-01-03
Will try this now :D.

---

### Post by vishalrao on 2010-01-03
Got quad boot eye candy working!

Just added the BURG karmic PPA (its been updated just a few days ago) and did aptitude update && aptitude safe-upgrade.

Then played with the sora theme, didn't work without some mucking about though :lolflag:

Check out my GRUB2 screenshot and youtube video!

[[img]http://www.imgx.org/thumbs/small/54333_ysgve/grub2-sora-theme.jpg[/img]](http://www.imgx.org/view/full/54333_ysgve)

vid: [http://www.youtube.com/watch?v=zBCR0jVzMFs](http://www.youtube.com/watch?v=zBCR0jVzMFs)

---

### Post by haytjes on 2010-01-03
> **vishalrao said:**
> Got something working.
Then played with the sora theme, didn't work without some mucking about though :lolflag:


Did you also have a font problem? (How did you solve it?)

---

### Post by vishalrao on 2010-01-03
yes, its trying to load helvetica-bold-27 and 29... so i just symlinked to the existing -24 one... and make sure the "loadfont ..." calls include them in the final generated grub.cfg :)

note i just added GRUB_THEME=sora to /etc/default/grub and not the ". /blah/theme.cfg" line to 40_custom... so i meddled around a bit...

i needed to add symlinks in /boot/grub to the font and sora folders in the /boot/grub/themes directory because either there is a bug or i misconfigured and its looking in /boot/grub instead of /boot/grub/themes ... HTH

---

### Post by k64 on 2010-01-03
Interestingly enough, [Mint]("http://www.linuxmint.com/") already had Grub2 before Ubuntu - and even Ubuntu 9.10 doesn't have a graphical boot menu. It will soon, though, and maybe 10.04 LTS will have GrubSplash?

---

### Post by vishalrao on 2010-01-03
im guessing Lucid (LTS) wont have it, though lucid+1 fo shizzle ma nizzle...

---

### Post by benjamimgois on 2010-01-03
That's very nice ! Ubuntu should have it !

---

### Post by Starks on 2010-01-03
vish, can you give a more specific walkthrough of the changes you needed to make?

---

### Post by KIAaze on 2010-01-03
I want the penguin bootloader!: [http://www.youtube.com/watch?v=0szKrjzXMw0](http://www.youtube.com/watch?v=0szKrjzXMw0)
:grin:

More seriously: Will such bootloaders be possible with grub2?
I remember seeing bootloader games somewhere once. :)

---

### Post by Starks on 2010-01-03
Penguin lemmings for a bootloader? I may just have to switch to OpenSUSE. </half-sarcasm>

---

### Post by vishalrao on 2010-01-03
> **Starks said:**
> vish, can you give a more specific walkthrough of the changes you needed to make?

ah i've run out of weekend time :( i'll get back to this later in the evening or perhaps during the weekend again, in the mean time will put a rough sequence from memory:

[LIST=1]
[*]add the burg karmic ppa (works for my kubuntu lucid install).
[*]run apt-get update && apt-get safe-upgrade (to replace grub-pc etc).
[*]download and extract sora theme so you have /boot/grub/themes/sora folder structure. also download the other "proto/ubuntu/winter" theme set to get /boot/grub/themes/fonts etc.
[*]create symlinks one level higher so you have /boot/grub/sora, /boot/grub/fonts etc (maybe i needed to do this coz i screwed up somewhere)
[*]in /etc/default/grub add "GRUB_THEME=sora", i also uncommented/added "GRUB_GFXMODE=1920x1200" for my monitor.
[*]just look at the files (theme.txt and theme.cfg etc) in the themes/sora folder to get an idea of whats going on inside.
[*]edit /etc/grub.d/10_linux, 30_os-prober, 40_custom etc scripts so that the generated "menuentry" lines in /boot/grub/grub.cfg have the part like "--class ubuntu" or "--class windows" or "--class arch" like "menuentry "Ubuntu xxxx" --class ubuntu { " so that the theme can pick the icons to match the OS! :) else it displays the generic "unknown" PNGs.
[*]edit /boot/grub/themes/sora/icons/icons.txt to include lines for your OS icons (i added for arch and fedora after making simple PNGs)
[*]run update-grub and inspect the generated /boot/grub/grub.cfg - check that you have "loadfont Helvetica-Bold-27.pnf2" etc lines in there.
[*]/boot/grub/themes/fonts only has helvetica bold 24 (for me) so i just added symlinks to it for sizes 27 and 29 which the theme seems to want to load.
[*]rerun update-grub if any last-minute fixes.
[*]reboot with fingers crossed :D
[*]if any problems (missing images, corrupt font, cant boot etc), just boot off live CD, follow "grub2 restore" partial steps to chroot into your install to continue editing to make more fixes and run update-grub.
[*]rinse and repeat, till you have your fresh smelling boot eye candy!
[/LIST]

BTW anyone tried the other grub2 experiemental PPA linked in a previous post by sevenmachines? got any other sweet-looking themes to try out?

---

### Post by bean123 on 2010-01-03
> **SevenMachines said:**
> burg uses a modified version of [colin bennetts gfxmenu ]("http://grub.gibibit.com/About")code. the original code has been merged into [grub experimental]("http://bzr.savannah.gnu.org/r/grub/branches/experimental/") if any brave souls are looking to play with it. it needed a little work the last time i checked but did work ok. 
i believe there was a long thread on this during the karmic release (and also in arch) and a few of the screenshots made it onto the [grub2 community documentation]("https://help.ubuntu.com/community/Grub2")

Yep, you're right. BURG's menu system is completely differently than Colin's. Colin's menu is basically an extension of existing menu, it just allows you to use fancy image. But BURG is much more, it allows you to control the behavior as well, such as define new keyboard hot-keys. There are also advanced features like customized password dialog, popup menu, multiple terminal window, terminal as edit box, etc.

BTW, binary package for Lucid would be available soon.

---

### Post by autocrosser on 2010-01-03
THANK YOU for jumping in bean!!!!  Please keep us advised as to when things will be available....I'm looking forward to testing it!!!!:guitar:

---

### Post by vishalrao on 2010-01-03
> **autocrosser said:**
> I'm looking forward to **testing** it!

No, I'm sure you mean "I'm looking forward to **playing** with it!" :lolflag:

---

### Post by autocrosser on 2010-01-04
Isn't testing=playing? :lolflag:

---

### Post by mkoehler on 2010-01-04
Looks sweet - I might have to fiddle around with it myself.  Is there still an option to fall back to the textual prompt if need be (say, to go into a RT kernel)?

---

### Post by bean123 on 2010-01-04
> **mkoehler said:**
> Looks sweet - I might have to fiddle around with it myself.  Is there still an option to fall back to the textual prompt if need be (say, to go into a RT kernel)?

Hotkeys defined in sora theme:

e - edit current menu command (ctrl-x to finish)
t - edit current menu title (ctrl-x to finish)
c - open terminal window (esc to quit)
2 - open two terminal windows (esc to quit, F6 to switch between them)
h - display help dialog
i - display about dialog
F8 - toggle between text and graphic mode
F9 - halt
F10 - reboot

---

### Post by Starks on 2010-01-04
I can't get this to work. Too many files to edit and still not enough info on what I need to do.

;_;

---

### Post by bean123 on 2010-01-04
> **Starks said:**
> I can't get this to work. Too many files to edit and still not enough info on what I need to do.

;_;

Actually with ppa5, the process is greatly simplified, you don't need to modify files any more. Here are the steps:

1, install ppa5, and install BURG to mbr/bs.
2, download theme files from the files section of

[http://groups.google.com/group/burg-devel](http://groups.google.com/group/burg-devel)

and extract to /boot/grub:

```

cd /boot/grub
sudo tar xzf ~/theme_default.tar.gz
sudo tar xzf ~/theme_sora.tar.gz
sudo tar xzf ~/theme_chiva.tar.gz

```

3, edit /boot/default/grub, add these two lines at the end:
```

GRUB_THEME=sora
GRUB_GFXMODE=1024x768

```

4, Run update-grub.

The value of GRUB_THEME can be one of these:
proto, ubuntu, winter, sora, sora/clean, sora/extended, chiva

---

### Post by Dayofswords on 2010-01-04
me wanty!

---

### Post by ppjose on 2010-01-04
[http://blog.lassehavelund.com/2010/grub-a-usability-hurdle-pt-2/](http://blog.lassehavelund.com/2010/grub-a-usability-hurdle-pt-2/)

[IMG]http://blog.lassehavelund.com/wp-content/uploads/2010/01/uboot.png[/IMG]


[IMG]http://blog.lassehavelund.com/wp-content/uploads/2010/01/uboot2.png[/IMG]

---

### Post by bean123 on 2010-01-04
> **ppjose said:**
> [http://blog.lassehavelund.com/2010/grub-a-usability-hurdle-pt-2/](http://blog.lassehavelund.com/2010/grub-a-usability-hurdle-pt-2/)

[IMG]http://blog.lassehavelund.com/wp-content/uploads/2010/01/uboot.png[/IMG]


[IMG]http://blog.lassehavelund.com/wp-content/uploads/2010/01/uboot2.png[/IMG]

Oh, it looks nice, and it shouldn't be difficult to implement it with BURG.

---

### Post by tuan.cse06 on 2010-01-04
I've installed that theme, but loading process is very slow.

---

### Post by bean123 on 2010-01-04
> **tuan.cse06 said:**
> I've installed that theme, but loading process is very slow.

Are you testing in qemu ? It should be pretty fast in virtualbox.

---

### Post by haytjes on 2010-01-04
My guide to a more beautiful grub (with a graphic mode check, so it shouldn't break):

1, install Burg: [https://help.ubuntu.com/community/Burg#Install%20using%20binary%20package](https://help.ubuntu.com/community/Burg#Install%20using%20binary%20package)
2, download theme files from the files section of

[http://groups.google.com/group/burg-devel](http://groups.google.com/group/burg-devel)

and extract to /boot/grub:

```

cd /boot/grub
sudo tar xzf ~/theme_default.tar.gz
sudo tar xzf ~/theme_sora.tar.gz
sudo tar xzf ~/theme_chiva.tar.gz

```

You definitely want to extract the first one, because it contains the fonts that Brug needs.

2, Restart your computer and press CTRL-C when grub shows. Use the command 'vbeinfo' to see the supported graphic modes.

3, Boot again and edit /etc/default/grub, add these two lines at the end:
```

GRUB_THEME=sora
GRUB_GFXMODE=1024x768

```

The value of GRUB_THEME can be one of these:
proto, ubuntu, winter, sora, sora/clean, sora/extended, chiva

The value of GRUB_GFXMODE must be a supported graphic mode of bullet 2.

4, Run update-grub.

5, Add bigger fonts
```

cd /boot/grub/fonts
sudo ln Helvetica-Bold-24.pf2 Helvetica-Bold-27.pf2
sudo ln Helvetica-Bold-24.pf2 Helvetica-Bold-29.pf2

```

6, Restart and hope for the best ;)

ps. If anything brakes in any stage: [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by vishalrao on 2010-01-04
> **bean123 said:**
> Oh, it looks nice, and it shouldn't be difficult to implement it with BURG.

Yes, good usability idea to group all entries for the same OS/distro under a common/single icon with a dropdown...

Now, any theme artists out there who want to try it? :D

---

### Post by meborc on 2010-01-04
> **haytjes said:**
> ...
4, Run update-grub.
...

shouldn't it be update-grub2?

---

### Post by haytjes on 2010-01-04
> **meborc said:**
> shouldn't it be update-grub2?

Here, it works with update-grub

---

### Post by Jenkins1 on 2010-01-04
I know what I am doing tonight  :-P

---

### Post by bean123 on 2010-01-04
> **haytjes said:**
> 
5, Add bigger fonts
```

cd /boot/grub/fonts
sudo ln Helvetica-Bold-24.pf2 Helvetica-Bold-27.pf2
sudo ln Helvetica-Bold-24.pf2 Helvetica-Bold-29.pf2

```


This step should not be necessary as ppa5 supports font autoloading. If you add new fonts, you also need to regenerate /boot/grub/fonts/font.lst using grub-mkfont.

---

### Post by drs305 on 2010-01-04
There appear to be two divergent ways of accomplishing the G2 theming - BURG and via Felix's ppa with Colin Bennet's [http://grub.gibibit.com/]("http://grub.gibibit.com/") site.

bean123, can you briefly describe the divergent approaches? And will the BURG theming method ever be able to use the 'official' G2 from the repositories at some point? I am leaping to an unfounded assumption that the Felix experimental G2 features will eventually be incorporated into the standard G2 package (which may be a bad assumption).  Are we about to kick off a GRUB v BURG war?

Also, I plan on adding this thread to the Theming section of my G2 Basics post, as we are finally getting enough documentation (at least in here) on how to go about using themes in Grub 2. 

It would be great if someone using Felix's experimental G2 ppa and Bennett's themes could detail the procedures for using those resources in a similar fashion to the BURG theming.

Also, since this thread is about Lucid, is anyone having success doing this in Karmic? If so, with which version of Grub 2?

Much thanks to all who have posted how they are accomplishing their theming.

---

### Post by haytjes on 2010-01-04
> **drs305 said:**
> Also, since this thread is about Lucid, is anyone having success doing this in Karmic? If so, with which version of Grub 2?


I've tried my tut on comment #32 for karmic and it works. (Version: 1.97+burg.20091210-2~ppa5)

---

### Post by Slug71 on 2010-01-04
Never heard of BURG til now. Is it meant to be a stand alone bootloader which can be used with Grub2 or is it meant to be an extension to Grub2?

Looks sweet though! :D

---

### Post by bean123 on 2010-01-04
> **drs305 said:**
> There appear to be two divergent ways of accomplishing the G2 theming - BURG and via Felix's ppa with Colin Bennet's [http://grub.gibibit.com/]("http://grub.gibibit.com/") site.

bean123, can you briefly describe the divergent approaches? And will the BURG method be able to use the 'official' G2 from the repositories at some point? I am leaping to an unfounded assumption that the Felix experimental G2 features will eventually be incorporated into the standard G2 package (which may be a bad assumption).

Also, I plan on adding this thread to the Theming section of my G2 Basics post, as we are finally getting enough documentation (at least in here) on how to go about using themes in Grub 2. 

It would be great if someone using Felix's experimental G2 ppa and Bennett's themes could detail the procedures for using those resources in a similar fashion to the BURG theming.

Also, since this thread is about Lucid, is anyone having success doing this in Karmic? If so, with which version of Grub 2?

Much thanks to all who have posted how they are accomplishing their theming.

I frequently merge with official grub repository, new feature in grub would be available in BURG as well. But BURG has make some dramatic change in code level, so it won't be able to incorporate back to G2 repository.

As for Colin's menu system, there is some unresolved issue:

1, Edit menu item not supported
2, Sub menu not supported
3, User defined hotkey not supported
4, Popup menu and dialog not supported
5, Terminal can only support fixed size font, BURG supports proportional font as well.

---

### Post by Jenkins1 on 2010-01-04
> **haytjes said:**
> My guide to a more beautiful grub (with a graphic mode check, so it shouldn't break):

1, install Burg: [https://help.ubuntu.com/community/Burg#Install%20using%20binary%20package](https://help.ubuntu.com/community/Burg#Install%20using%20binary%20package)
2, download theme files from the files section of

[http://groups.google.com/group/burg-devel](http://groups.google.com/group/burg-devel)

and extract to /boot/grub:

```

cd /boot/grub
sudo tar xzf ~/theme_default.tar.gz
sudo tar xzf ~/theme_sora.tar.gz
sudo tar xzf ~/theme_chiva.tar.gz

```

You definitely want to extract the first one, because it contains the fonts that Brug needs.

2, Restart your computer and press CTRL-C when grub shows. Use the command 'vbeinfo' to see the supported graphic modes.

3, Boot again and edit [COLOR="Red"]/boot[/COLOR]/default/grub, add these two lines at the end:
```

GRUB_THEME=sora
GRUB_GFXMODE=1024x768

```

The value of GRUB_THEME can be one of these:
proto, ubuntu, winter, sora, sora/clean, sora/extended, chiva

The value of GRUB_GFXMODE must be a supported graphic mode of bullet 2.

4, Run update-grub.

5, Add bigger fonts
```

cd /boot/grub/fonts
sudo ln Helvetica-Bold-24.pf2 Helvetica-Bold-27.pf2
sudo ln Helvetica-Bold-24.pf2 Helvetica-Bold-29.pf2

```

6, Restart and hope for the best ;)

ps. If anything brakes in any stage: [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

I have this tutorial working in karmic as well. Should it not be "etc" not "boot" (added red high lighting) at least this was the case for me.

---

### Post by drs305 on 2010-01-04
> **Jenkins1 said:**
> I have this tutorial working in karmic as well. Should it not be "etc" not "boot" (added red high lighting) at least this was the case for me.

Yes, it should be /etc/default/grub.

haytjes, 
nice instructions (with the address change above). Worked fine for me in Karmic 64-bit VM using the Ubuntu theme. Score one for BURG.  

Note: The Grub devs indicate that once they get themes worked out in Grub 2 it will be just a matter of installing themes just as you install any other package/deb.

---

### Post by dyltman on 2010-01-04
> **tuan.cse06 said:**
> I've installed that theme, but loading process is very slow.

any guide on how to?

---

### Post by vishalrao on 2010-01-04
> **meborc said:**
> shouldn't it be update-grub2?

i believe update-grub2 is now moved to update-grub and its now just a different script thats calls update-grub anyway - if you just "cat `which update-grub`" and "cat `update-grub2`" to look at the contents... :)

---

### Post by ranch hand on 2010-01-04
> **meborc said:**
> shouldn't it be update-grub2?
No it should not.

The "update-grub2" command was a temporary hack for 1.96 so that people would not screw with the Ubuntu alpha grub2 on Karmic alpha2.  It has not been needed for a long time back into the 9.10 pre-release days.  It still works (I think) but only because it hasn't been fixed (why remove it?).

I wish folks would quit referring to it, it is clumsy and obsolete.

---

### Post by bean123 on 2010-01-07
Update for ppa6:

New tool grub-emu, support live preview from Linux/Windows/OSX.

Installation notes for ubuntu karmic:

1, Install package

Add these lines to /etc/apt/sources.list:

Ubuntu Karmic:
```

deb http://ppa.launchpad.net/bean123ch/burg/ubuntu karmic main
deb-src http://ppa.launchpad.net/bean123ch/burg/ubuntu karmic main

```

Ubuntu Lucid:
```

deb http://ppa.launchpad.net/bean123ch/burg/ubuntu lucid main
deb-src http://ppa.launchpad.net/bean123ch/burg/ubuntu lucid main

```

then install the package:
```

sudo apt-get update
sudo apt-get install grub-pc

```

If you want to avoid the warning about unknown signature, use these commands to import it:
```

gpg --keyserver subkeys.pgp.net --recv 55708F1EE06803C5
gpg --export --armor 55708F1EE06803C5 | sudo apt-key add -

```

Then, you need to install the new boot loader to mbr, for example:
```

sudo grub-install "(hd0)"

```
Change hd0 if you want to install to other disk.

2, Download themes

Download theme file from:

[http://code.google.com/p/burg/downloads/list](http://code.google.com/p/burg/downloads/list)

theme_fonts.zip is the common font files, theme_*.zip contains individual theme. After download, extract it to /boot/grub, for example:
```

cd /boot/grub
sudo unzip ~/theme_fonts.zip
sudo unzip ~/theme_sora.zip

```

3, Edit config file

edit /etc/default/grub, GRUB_THEME is the theme name, GRUB_GFXMODE is the screen resolution, for example:

```

GRUB_THEME=sora
GRUB_GFXMODE=1024x768

```

Since 1.97+burg.20100110-1~ppa6, it also supports option GRUB_FOLD, which is used to fold all linux boot items into one. To show the complete list, use some hot-keys defined in theme, for example F7. I've created a refit theme to illustrate this feature:

```

GRUB_THEME=refit
GRUB_GFXMODE=640x480
GRUB_FOLD=1

```

Then, use the following command to generate grub.cfg:
```

sudo update-grub

```

It's done, the new boot loader will be used after you reboot. Although, you can also live preview the theme using grub-emu.

4, Use grub-emu

First, install grub-emu:
```

sudo apt-get install grub-emu

```

Use this command to preview the theme inside Linux:
```

sync ; sudo grub-emu

```

Keyboard works inside the emulated window. To quit, open a console windows with 'c', then enter command 'halt' or 'exit'. You can also use the hot-key F9, which maps to the halt command.

You can also use a test directory. This way, you don't need to be super user to run grub-emu. First, create a test directory, and extract fonts and theme files to it. Then, construct a configuration file grub.cfg, for example:
```

menuentry "Windows" --class Windows --submenu menu_Windows {
  true
}

menuentry "Windows Two" --class Windows --menu menu_Windows {
  true
}

menuentry "Windows Three" --class Windows --menu menu_Windows {
  true
}

menuentry "Linux" --class Linux {
  true
}

menuentry "OSX" --class MacOSX {
  true
}

set timeout=10

# For normal theme
#set gfxmode=800x600
#set gfxfont="Unifont Regular 16"
#set theme_dir=${prefix}/themes/ubuntu
#load_config ${theme_dir}/theme.txt
#menu_region.text
#menu_region.gfx
#menu_viewer.ext

# For sora theme
. ${prefix}/themes/sora/theme.cfg

```

To test sora theme, uncomment the lower section. To test normal theme, uncomment the upper section, and change ubuntu to the name of the theme you're testing.

This config also shows how to test the new folding feature. The first item which would appear in main menu should have a --submenu option, subsequent items which would be folded would have a --menu option with the same id.
 
Finally, run this inside the test directory:
```

grub-emu -r host -d .

```

Similar test method can be used in Windows as well. I've uploaded  binary package grub-emu_win32_ppa6.zip in download page, extract to the test directory, then double click run.cmd to start the application.

---

### Post by McDuff on 2010-01-07
this looks very promising.
two issues i have:

- i have to hit <tab> before being able to browse the entries with cursor keys
- in default install on ubuntu the only place where adding &#8220;--class Ubuntu&#8221; would have an effect is in grub.cfg on which editing is deprecated. so there should rather be an extension to the script 10_linux to determine the present distributions and add the appropriate class to the entries.

what's more, since the update to ppa6, the opensuse entries show no icons at all (before they showed the &#8220;unknown os&#8221;-icon.

---

### Post by bean123 on 2010-01-07
> **McDuff said:**
> this looks very promising.
two issues i have:

- i have to hit <tab> before being able to browse the entries with cursor keys

Yep, you need to switch input focus from terminal window to the SDL window.

> 
- in default install on ubuntu the only place where adding “--class Ubuntu” would have an effect is in grub.cfg on which editing is deprecated. so there should rather be an extension to the script 10_linux to determine the present distributions and add the appropriate class to the entries.


Right, I think 10_linux should be smart enough to detect the distribution. Any idea how to get the OS name ?

> 
what's more, since the update to ppa6, the opensuse entries show no icons at all (before they showed the “unknown os”-icon.
Now burg uses the result of os-prober to set the --class parameter (previously it's empty). However, sora theme doesn't include icons for some OS, but it's quite easy to add. Add the system icon to icons directory, then edit icons/icons.txt, add the entry for your OS. You can examine the generated grub.cfg to decide which OS label to use.

---

### Post by bean123 on 2010-01-07
BURG ppa6 binary package for lucid now available in launchpad.

---

### Post by meborc on 2010-01-07
> **vishalrao said:**
> i believe update-grub2 is now moved to update-grub and its now just a different script thats calls update-grub anyway - if you just "cat `which update-grub`" and "cat `update-grub2`" to look at the contents... :)

> **ranch hand said:**
> No it should not.

The "update-grub2" command was a temporary hack for 1.96 so that people would not screw with the Ubuntu alpha grub2 on Karmic alpha2.  It has not been needed for a long time back into the 9.10 pre-release days.  It still works (I think) but only because it hasn't been fixed (why remove it?).

I wish folks would quit referring to it, it is clumsy and obsolete.

thanks guys, i did not know that...

---

### Post by vishalrao on 2010-01-07
> **bean123 said:**
> Right, I think 10_linux should be smart enough to detect the distribution. Any idea how to get the OS name ?

I just edited those scripts, 10_linux, 30_os-prober and 40_custom so that it adds the bolded part " menuentry "blah" **--class os_name** { " based on the partition labels which i added via gparted for windows, ubuntu, fedora and arch...

not sure if this will get overwritten with the next set of updates or if it will even prompt to merge...

---

### Post by McDuff on 2010-01-07
> **bean123 said:**
> Yep, you need to switch input focus from terminal window to the SDL window.

i haven't noticed any message that tell me to use <tab> to do so. perhaps this should be added?

> 
Right, I think 10_linux should be smart enough to detect the distribution. Any idea how to get the OS name ?

sadly, i do not really have an idea of programming but i could imagine  10_linux to parse the title lines which usually contain the distribution's name to match the strings in a list of distribution names and add the appropriate class parameter, and if no match is found, add generic class linux.

> 
Now burg uses the result of os-prober to set the --class parameter (previously it's empty). However, sora theme doesn't include icons for some OS, but it's quite easy to add. Add the system icon to icons directory, then edit icons/icons.txt, add the entry for your OS. You can examine the generated grub.cfg to decide which OS label to use.

i've looked into grub.cfg and found out, that os-prober set --class SuSE, which it found to be the variable OSLABEL. what would ubuntu provide as OSLABEL? has anybody tried that? does every linux distribution provide a similar one? thus no linux distribution would be --classified as linux so none shows an icon but those few in the theme?

---

### Post by khabu on 2010-01-07
If you look in the 10_linux script, there's a variable called GRUB_DISTRIBUTOR.

So at line 62, that's the line in my file, you'll see this line

printf "menuentry \"${title}\" --class [COLOR="Red"]**Linux**[/COLOR] {\n" "${os}"

Replace Linux with [COLOR="Blue"]**${GRUB_DISTRIBUTOR}**[/COLOR] and it should replace it with the right distro.  I only have Ubuntu so i'm not sure if it works with other distros, but it works for Ubuntu.

Now my problem is that none of the images are showing up. All the text shows up, but none of the images.  I can get it going for the sora theme, but the menu looks messed up.  Anyone else having this problem?

EDIT: Figured it out. For sora you have to take out the comment for GRUB_TERMINAL=console and add the line . /boot/grub/themes/sora/theme.cfg in the 40_custom script. But for any of the other themes you comment out GRUB_TERMINAL=console and leave out the line for the sora config.

---

### Post by bean123 on 2010-01-08
> **McDuff said:**
> i haven't noticed any message that tell me to use <tab> to do so. perhaps this should be added?

Oh, I misunderstand you the last time. Actually, the <tab> issue is an issue of the sora theme, it has a small system icon on top, which gets input focus when at startup. Therefore, you need to use <tab> or <down> to select the second row. This is not difficult to fix.

> 
i've looked into grub.cfg and found out, that os-prober set --class SuSE, which it found to be the variable OSLABEL. what would ubuntu provide as OSLABEL? has anybody tried that? does every linux distribution provide a similar one? thus no linux distribution would be --classified as linux so none shows an icon but those few in the theme?

Unfortunately, os-prober don't detect the current os, so it can't use OSLABEL to decide OS name. However, the ${GRUB_DISTRIBUTOR} solution khabu described works well.

---

### Post by Starks on 2010-01-08
I'm getting the Tux logo for Lucid. I want the Ubuntu logo.

---

### Post by bean123 on 2010-01-08
> **khabu said:**
> If you look in the 10_linux script, there's a variable called GRUB_DISTRIBUTOR.

So at line 62, that's the line in my file, you'll see this line

printf "menuentry \"${title}\" --class [COLOR="Red"]**Linux**[/COLOR] {\n" "${os}"

Replace Linux with [COLOR="Blue"]**${GRUB_DISTRIBUTOR}**[/COLOR] and it should replace it with the right distro.  I only have Ubuntu so i'm not sure if it works with other distros, but it works for Ubuntu.

Thanks a lot for the tip, I would modify 10_linux to use ${GRUB_DISTRIBUTOR} in the next version.

> 
Now my problem is that none of the images are showing up. All the text shows up, but none of the images.  I can get it going for the sora theme, but the menu looks messed up.  Anyone else having this problem?

EDIT: Figured it out. For sora you have to take out the comment for GRUB_TERMINAL=console and add the line . /boot/grub/themes/sora/theme.cfg in the 40_custom script. But for any of the other themes you comment out GRUB_TERMINAL=console and leave out the line for the sora config.

With GRUB_TERMINAL=console, it starts in text mode instead of graphic mode, so you should always comment it out. The sora theme should work with GRUB_THEME, you don't need to change 40_custom script directly.

---

### Post by bean123 on 2010-01-08
Just upload a new version of ppa6 that detect Ubuntu properly in 10_linux, should be available in a few hours.

The build is complete now, package name 1.97+burg.20100108-1~ppa6, available for both karmic and lucid.

---

### Post by bean123 on 2010-01-08
> **bean123 said:**
> Oh, I misunderstand you the last time. Actually, the <tab> issue is an issue of the sora theme, it has a small system icon on top, which gets input focus when at startup. Therefore, you need to use <tab> or <down> to select the second row. This is not difficult to fix.

After some checking, the sora theme does the right thing and put input focus in the icon row at start-up, I think you may have used up/down key to stop the timeout, which move input to the tools icon at the same time.

---

### Post by Netich on 2010-01-08
bean123, congratulations for your work. Maybe its just one second, but for some people (I always think in my father for usability issues :) ) GRUB can be that black screen where you dont have to touch anything or you'll break the computer.

So two big logos is the way to go, without losing all the potential Grub have (terminal, several linux kernels, memtest...)

Just two questions:
- I have some flickering in sora theme. I dont know if its related to my cheap intel GPU though...

- XP get the windows logo for me, but Windows 7 (W7 loader in fact) dont get any logo. I dont know if i should uninstall W7 loader, but i would prefer to have it there just in case (with 0 seconds), and BURG to detect the loader and put the W7 logo.

---

### Post by bean123 on 2010-01-08
> **Netich said:**
> 
- I have some flickering in sora theme. I dont know if its related to my cheap intel GPU though...

Sora theme is quite complicated and have many bitmaps, so it could run a little slow on some machine. Themes like ubuntu is pretty fast though. Also, grub-emu may flicker a bit in Linux, but it runs quite smooth on Windows (could be caused by different SDL implementation).

> 
- XP get the windows logo for me, but Windows 7 (W7 loader in fact) dont get any logo. I dont know if i should uninstall W7 loader, but i would prefer to have it there just in case (with 0 seconds), and BURG to detect the loader and put the W7 logo.
It depends on os-prober to detect OS, perhaps os-prober doesn't get it right, or maybe it uses a different label for W7. You can open /boot/grub/grub.cfg and see what's the --class value of W7 entry.

---

### Post by shafin on 2010-01-08
> **bean123 said:**
> After some checking, the sora theme does the right thing and put input focus in the icon row at start-up, I think you may have used up/down key to stop the timeout, which move input to the tools icon at the same time.
I can confirm this bug. Even if I use left/right keys to stop the timeout, I need to press tab/down to get focus to OS chooser box.

BTW, BURG is a great piece of software, thanks a lot bean123.

---

### Post by McDuff on 2010-01-08
> **bean123 said:**
> After some checking, the sora theme does the right thing and put input focus in the icon row at start-up, I think you may have used up/down key to stop the timeout, which move input to the tools icon at the same time.

ok, i rebooted four times now to be really sure. input focus is definitely not on the tool icon, that's right, yet there is no reaction on left/right keys. i have to hit <tab> twice, first to put focus on the tool icon, then to put focus on the icon row, only then left/right keys show the expected reaction.

---

### Post by bean123 on 2010-01-08
> **McDuff said:**
> ok, i rebooted four times now to be really sure. input focus is definitely not on the tool icon, that's right, yet there is no reaction on left/right keys. i have to hit <tab> twice, first to put focus on the tool icon, then to put focus on the icon row, only then left/right keys show the expected reaction.

Have you set the value of GRUB_DEFAULT ? BTW, does this also happen in grub-emu ?

---

### Post by zet120 on 2010-01-08
Hi,
Until yesterday everything OK ...
Grub is installed on a partition /dev/sda4 theme Chiva - ok
Today, when you auto-update to version (1.97+burg.20100108-1~ppa6) i have a problem.
Grub will not install on the partition /dev/sda4 (or root) is not mbr, mbr=Chameleon:
Disk GPT/mbr
```
zet120@zet120-desktop:~$ sudo grub-install --force  "(hd0,4)"
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
Segmentation fault

```
Any idea?

---

### Post by McDuff on 2010-01-08
> **bean123 said:**
> Have you set the value of GRUB_DEFAULT ? BTW, does this also happen in grub-emu ?

i have left all the scripts like they came except for adding the themeand changing gfxmode to 1680x1050

GRUB_DEFAULT=0 (what does this mean?)

this does not happen in grub-emu, but there it accepts keystrokes only after the timeout.

---

### Post by bean123 on 2010-01-08
> **McDuff said:**
> i have left all the scripts like they came except for adding the themeand changing gfxmode to 1680x1050

GRUB_DEFAULT=0 (what does this mean?)

this does not happen in grub-emu, but there it accepts keystrokes only after the timeout.

Very odd indeed. Perhaps you can try some other themes as well and see if there is similar issue.

---

### Post by McDuff on 2010-01-08
> **bean123 said:**
> Very odd indeed. Perhaps you can try some other themes as well and see if there is similar issue.

same thing with theme ubuntu. only <tab> interrupts the timeout, cursor has no effect.

---

### Post by bean123 on 2010-01-08
> **zet120 said:**
> Hi,
Until yesterday everything OK ...
Grub is installed on a partition /dev/sda4 theme Chiva - ok
Today, when you auto-update to version (1.97+burg.20100108-1~ppa6) i have a problem.
Grub will not install on the partition /dev/sda4 (or root) is not mbr, mbr=Chameleon:
Disk GPT/mbr
```
zet120@zet120-desktop:~$ sudo grub-install --force  "(hd0,4)"
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
Segmentation fault

```
Any idea?

I've tracked down a regression in recent code, you can try replacing /usr/sbin/grub-setup with the one from attachment and see if it works.

---

### Post by zet120 on 2010-01-08
Yes, it is working.;)
```

zet120@zet120-desktop:~$ sudo grub-install --force /dev/sda4
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
Installation finished. No error reported.

```
sora - OK
chiva - OK

Thanks.;)

---

### Post by bean123 on 2010-01-08
> **McDuff said:**
> same thing with theme ubuntu. only <tab> interrupts the timeout, cursor has no effect.

Yep, I've found the problem for grub-emu, this one should work now.

BTW, I also make a small improvement, now you can quit grub-emu by clicking the close button in SDL window.

---

### Post by khabu on 2010-01-08
It seems grub doesn't respond to keyboard commands right away when loading.  When I apply any theme, after hitting up,down,left, or right I have to wait about 2 seconds before it does anything.

---

### Post by bean123 on 2010-01-09
New package 1.97+burg.20100109-1~ppa6 for karmic

Several optimization and bug fixes, now sora theme should runs faster, and flicker should be gone.

---

### Post by Netich on 2010-01-09
Yep, flicker is gone, and it seems to load faster. Entering in the menu (the tools icon) is a bit slow but since that is hardly used in a normal boot, i think is its low prority.

Excelent work, mate  =D>

---

### Post by cecilpierce on 2010-01-09
How do I get the OS icons ? All I get is the text mode.

---

### Post by bean123 on 2010-01-09
> **cecilpierce said:**
> How do I get the OS icons ? All I get is the text mode.

Edit /etc/default/grub, set GFX_THEME to theme name, and make sure GRUB_TERMINAL=console is commented out. The run update-grub.

---

### Post by cecilpierce on 2010-01-09
Here is what is in /etc/default/grub:

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
GRUB_DISABLE_LINUX_RECOVERY="true"
GRUB_THEME=sora
GRUB_GFXMODE=1280x1024

---

### Post by gjoellee on 2010-01-09
> **vishalrao said:**
> I've come across the following cool stuff about GRUB2 theming:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

This just blew me away: [http://ubuntuguide.net/add-os-logos-into-grub2-boot-menu-using-burg](http://ubuntuguide.net/add-os-logos-into-grub2-boot-menu-using-burg) :guitar:

I tried using the themes without installing BURG but didnt seem to work so I guess its not merged back into upstream GRUB and I need to add the BURG repos.

I am currently trying out the ubuntu2 theme from [http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg](http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg) but this might also need BURG...

oh well, hoping for some nice boot loader eye candy for lucid - if not official then community based...

What about getting BLURG into Ubuntu be default? I have not tried it, so I don't know if it is stable enough etc...

---

### Post by tad1073 on 2010-01-09
I followed the tutorial here : [http://ubuntuguide.net/add-os-logos-into-grub2-boot-menu-using-burg](http://ubuntuguide.net/add-os-logos-into-grub2-boot-menu-using-burg)

I keep getting this error:

```
sudo update-grub
Generating grub.cfg ...
Theme file not found.

```

---

### Post by Starks on 2010-01-09
> **tad1073 said:**
> I followed the tutorial here : [http://ubuntuguide.net/add-os-logos-into-grub2-boot-menu-using-burg](http://ubuntuguide.net/add-os-logos-into-grub2-boot-menu-using-burg)

I keep getting this error:

```
sudo update-grub
Generating grub.cfg ...
Theme file not found.

```
You didn't follow the tutorial then. ;)

The official tutorial is a few pages back. Maybe you'll have better luck. Swap karmic for lucid in the repo lines or use ppa:bean123ch/burg.
[http://ubuntuforums.org/showpost.php?p=8623952&postcount=47](http://ubuntuforums.org/showpost.php?p=8623952&postcount=47)

---

### Post by tad1073 on 2010-01-10
> **Starks said:**
> You didn't follow the tutorial then. ;)

The official tutorial is a few pages back. Maybe you'll have better luck. Swap karmic for lucid in the repo lines or use ppa:bean123ch/burg.
[http://ubuntuforums.org/showpost.php?p=8623952&postcount=47](http://ubuntuforums.org/showpost.php?p=8623952&postcount=47)

thanks, I went back and retraced everything, works fine now.

---

### Post by bean123 on 2010-01-10
New package 1.97+burg.20100110-1~ppa6, karmic and lucid.

Support folding boot items. To enable it, set GRUB_FOLD=1 in /etc/default/grub, for example:

```

GRUB_THEME=refit
GRUB_GFXMODE=640x480
GRUB_FOLD=1

```

refit is a new theme I created to illustrate the folding function, it can be downloaded from

[http://code.google.com/p/burg/downloads/list](http://code.google.com/p/burg/downloads/list).

It only shows one item for linux, press enter and it boots the default item. You can also uses F7 key to see the complete item list.

---

### Post by tad1073 on 2010-01-10
Nice work.

> **bean123 said:**
> New package 1.97+burg.20100110-1~ppa6, karmic and lucid.

Support folding boot items. To enable it, set GRUB_FOLD=1 in /etc/default/grub, for example:

```

GRUB_THEME=refit
GRUB_GFXMODE=640x480
GRUB_FOLD=1

```refit is a new theme I created to illustrate the folding function, it can be downloaded from

[http://code.google.com/p/burg/downloads/list](http://code.google.com/p/burg/downloads/list).

It only shows one item for linux, press enter and it boots the default item. You can also uses F7 key to see the complete item list.

---

### Post by vishalrao on 2010-01-10
Now we're getting there! Just need some stock icons of the same size (hover non hover) and we're set! Right now I'm using my own ones tweaked in GIMP - not very pretty :)

---

### Post by Starks on 2010-01-10
BURG better be adopted by Canonical or merged into GRUB master for Lucid or Mystic.

---

### Post by ranch hand on 2010-01-10
> **Starks said:**
> BURG better be adopted by Canonical or merged into GRUB master for Lucid or Mystic.
I would not want that as my default screen and there are probably other taste impaired folks out there that would still prefer the text style menu.

It certainly looks like a pretty nice piece of work to me though.

---

### Post by Starks on 2010-01-10
For Linux newbies, the GRUB menu is the scariest moment of a bootup. Sure, one could dual-boot and keep the Windows OS selection menu, but shouldn't it be a goal to give GRUB a much needed user-friendly option (not necessarily default)? The OpenSUSE devs realized this and adopted the gfxmenu/gfxboot branches for GRUB.

---

### Post by ranch hand on 2010-01-10
Ah, the user friendly argument.  I will have to say that you may be right.

This is, however, very subjective.  In my case I found the text menu extremely comfortable.  This may well be due to my early experience with MSdos menus.

I find the graphic style menu in burg very irritating.  It is very like the one used in Mandriva and I, personally, find it clunky as it actually takes longer to wade through to what I want on my admittedly unusually over populated system.

This, of coarse, would probably not be the case with a "newbie".  There again my set up has never conformed to the assumed noobs set up.  I never dual booted with MS.  I did dual boot in the first week of Hardy with another Hardy so that I could break the thing with out effecting the install that we actually were trying to use (seemed to the wife that it should run for as long as a day without breaking - unreasonable woman).

This meant on the text menu that all I had to do was click on the version "playtime" or use the default "hardy".  With the graphical style I would have to go through the extra step of clicking on the logo and then select the version.  This, to me, is not user friendly it is just another layer to wade through.

---

### Post by cdEWoozy on 2010-01-10
> **ranch hand said:**
> Ah, the user friendly argument.  I will have to say that you may be right.
User friendliness is without doubt very important, but it doesn't mean it can only be achieved graphically :)

Martin Owens wrote a blog entry about [grub2 usability](http://doctormo.wordpress.com/2010/01/09/grub2-usability/) two days ago.

---

### Post by vishalrao on 2010-01-10
Lucid should at least have a simple background to start with - it looks like safe/doable to me - unless I'm missing the reason why they've never had a simple GRUB background so far (like say Fedora's simple one). I can wait til Lucid+1 for official bootloader bling. Those of us impatient can simply add PPA like we are doing for Karmic anyways...

edit: i followed the links on that blog to directxhex and lasse havelund. lasse has posted to ayatana list about grub2 theming asking it to be considered for lucid or lucid+1 , i hope more discussion move ahead: [https://lists.launchpad.net/ayatana/msg00941.html](https://lists.launchpad.net/ayatana/msg00941.html)

---

### Post by bean123 on 2010-01-11
> **ranch hand said:**
> Ah, the user friendly argument.  I will have to say that you may be right.

This is, however, very subjective.  In my case I found the text menu extremely comfortable.  This may well be due to my early experience with MSdos menus.

I find the graphic style menu in burg very irritating.  It is very like the one used in Mandriva and I, personally, find it clunky as it actually takes longer to wade through to what I want on my admittedly unusually over populated system.

This, of coarse, would probably not be the case with a "newbie".  There again my set up has never conformed to the assumed noobs set up.  I never dual booted with MS.  I did dual boot in the first week of Hardy with another Hardy so that I could break the thing with out effecting the install that we actually were trying to use (seemed to the wife that it should run for as long as a day without breaking - unreasonable woman).

This meant on the text menu that all I had to do was click on the version "playtime" or use the default "hardy".  With the graphical style I would have to go through the extra step of clicking on the logo and then select the version.  This, to me, is not user friendly it is just another layer to wade through.

BURG supports old text menu as well, just comment out GRUB_THEME option, and it behaves the same as old grub.

And actually, one of BURG's strength is that it's configurable. For grub, you're stick with what programmer has designed, but with BURG, you can design your own ui. For example, you can place the boot menu anywhere you want, or define hot-keys to do certain function. And BURG support both text and graphic mode. A well designed theme can work in both mode, and you can use a hot-key to switch between them.

---

### Post by Ibidem on 2010-01-11
I'm sure plenty of folks disagree with me (I login in text mode, if that indicates anything to you), but I personally agree with ranch hand that text mode is more comfortable for the menu.
Not that we should think about Microsoft, but if anyone here has seen the Windows bootloader, it's not very different from GRUB in appearance (barring the boxed menu for GRUB)
Then  come the questions:
1.  How does it handle "rescue" type stuff?
If I press "c", do I still get the GRUB command line?
That is how I installed Lucid.
And edit mode frequently comes in handy.
2.  How does it work with ramdisks?
A classic trick for BIOS flashing is use GRUB to load memdisk to boot DOS to flash the BIOS.
With grub4dos, it was even possible to load the ramdisk and DOS kernel directly (not kidding).
I expect it would work, but the graphics might complicate things here.
3.  How portable is graphics mode?
There are the old cards that refuse to work "nicely"; some (ancient) ones required oddball graphics mode stuff; and then you have headless systems to deal with.
4.  How does it "scale"?
If I keep the ~10 entries I presently have in GRUB 2 or add a few more, what does this do?
Will it error, take me forever to sort through, or have a screen full of icons?
5.  What filesystems work?
Is it the same as GRUB2 here, or different?  Haven't tried in GRUB2 yet, but I've booted Linux from NTFS (really funny when I use that to shrink the partition...) with grub4dos.

I would say that if such a thing is included, theming should not be turned on by default in an alternate install.
Ibidem

---

### Post by bean123 on 2010-01-11
> **Ibidem said:**
> I'm sure plenty of folks disagree with me (I login in text mode, if that indicates anything to you), but I personally agree with ranch hand that text mode is more comfortable for the menu.
Not that we should think about Microsoft, but if anyone here has seen the Windows bootloader, it's not very different from GRUB in appearance (barring the boxed menu for GRUB)
Then  come the questions:
1.  How does it handle "rescue" type stuff?
If I press "c", do I still get the GRUB command line?
That is how I installed Lucid.
And edit mode frequently comes in handy.

Of course it works, you can even edit the title of boot item with 't' hot-key. BTW, the gfxmenu in grub experiment doesn't implement edit mode.


> 
2.  How does it work with ramdisks?
A classic trick for BIOS flashing is use GRUB to load memdisk to boot DOS to flash the BIOS.
With grub4dos, it was even possible to load the ramdisk and DOS kernel directly (not kidding).
I expect it would work, but the graphics might complicate things here.

it should work.

> 
3.  How portable is graphics mode?
There are the old cards that refuse to work "nicely"; some (ancient) ones required oddball graphics mode stuff; and then you have headless systems to deal with.

You can use F8 to switch back to text mode if graphic mode doesn't work well.

> 
4.  How does it "scale"?
If I keep the ~10 entries I presently have in GRUB 2 or add a few more, what does this do?
Will it error, take me forever to sort through, or have a screen full of icons?

BURG is quite scalable. There are size units like percentage that works in different resolution. And layout manger is responsible for placing widgets on screen.

> 
5.  What filesystems work?
Is it the same as GRUB2 here, or different?  Haven't tried in GRUB2 yet, but I've booted Linux from NTFS (really funny when I use that to shrink the partition...) with grub4dos.

I would say that if such a thing is included, theming should not be turned on by default in an alternate install.
Ibidem

Yes it works, in fact, the NTFS reader in grub4dos and grub2 are both written by me.

---

### Post by Netich on 2010-01-11
> **cdEWoozy said:**
> User friendliness is without doubt very important, but it doesn't mean it can only be achieved graphically :)

Martin Owens wrote a blog entry about [grub2 usability](http://doctormo.wordpress.com/2010/01/09/grub2-usability/) two days ago.

Thats true, i think folding adds more to usability than graphics. For a noob, various kernels and recoveries, are not necessary. Just give them the first entry with the name of the distribution, and an option to go to advanced.

---

### Post by McDuff on 2010-01-11
> **bean123 said:**
> New package 1.97+burg.20100110-1~ppa6, karmic and lucid.

Support folding boot items. To enable it, set GRUB_FOLD=1 in /etc/default/grub, for example:

```

GRUB_THEME=refit
GRUB_GFXMODE=640x480
GRUB_FOLD=1

```

refit is a new theme I created to illustrate the folding function, it can be downloaded from

[http://code.google.com/p/burg/downloads/list](http://code.google.com/p/burg/downloads/list).

It only shows one item for linux, press enter and it boots the default item. You can also uses F7 key to see the complete item list.

this is really great!

sadly i'm having the same issue with refit as i have with sora: i have to hit <tab> twice before arrow-keys show any effect. is this possibly a driver issue? the other keys work as they should (letters, F7 etc.).

my mainboard is m2n-vm dh, the keyboard is attached via ps/2.

---

### Post by bean123 on 2010-01-11
> **McDuff said:**
> this is really great!

sadly i'm having the same issue with refit as i have with sora: i have to hit <tab> twice before arrow-keys show any effect. is this possibly a driver issue? the other keys work as they should (letters, F7 etc.).

my mainboard is m2n-vm dh, the keyboard is attached via ps/2.

Yep, it's possible that this is a HW related issue, I can't reproduce it in my testing machines.

BTW, does it select the first icon at startup ? How about timeout, if you don't press any key, does it boot into system after timeout ?

---

### Post by McDuff on 2010-01-11
> **bean123 said:**
> Yep, it's possible that this is a HW related issue, I can't reproduce it in my testing machines.

BTW, does it select the first icon at startup ? How about timeout, if you don't press any key, does it boot into system after timeout ?

yes, the first icon is selected at startup (in sora as well as in refit).
if i don't press any key (or press an arrow key), timeout finishes normally and system starts normally. any other key interrupts the timeout.

---

### Post by bean123 on 2010-01-11
> **McDuff said:**
> yes, the first icon is selected at startup (in sora as well as in refit).
if i don't press any key (or press an arrow key), timeout finishes normally and system starts normally. any other key interrupts the timeout.

Perhaps you can try the old menu as well. Comment out GRUB_THEME option, and use update-grub to update grub.cfg. This should allow you to boot into the old grub menu. See if it has similar issue.

---

### Post by phillw on 2010-01-11
Hi,

I've been following the thread.. Does burg like grub v1.98, which "hit the shops" today ? I ask, as I've been more closely following grub v1.97beta --> 1.97 --> 1.98 because of issues with RAID, which I believe is absolutely essential for a LTS (especially server-side) and the devs have been concentrating on that, possibly to the detriment of "eye-candy". Nice boot screens are lovely - once the important stuff works.

Regards,

Phill.

---

### Post by bean123 on 2010-01-12
> **phillw said:**
> Hi,

I've been following the thread.. Does burg like grub v1.98, which "hit the shops" today ? I ask, as I've been more closely following grub v1.97beta --> 1.97 --> 1.98 because of issues with RAID, which I believe is absolutely essential for a LTS (especially server-side) and the devs have been concentrating on that, possibly to the detriment of "eye-candy". Nice boot screens are lovely - once the important stuff works.

Regards,

Phill.

The last merge is from grub r2022, 2010-01-03, I don't think there is any change in raid code since then.

And BTW, since you mention raid, I'm just about to resolve some issue on the lvm/raid setup, although I think it's better to start a new thread on this.

---

### Post by McDuff on 2010-01-12
> **bean123 said:**
> Perhaps you can try the old menu as well. Comment out GRUB_THEME option, and use update-grub to update grub.cfg. This should allow you to boot into the old grub menu. See if it has similar issue.

no problem with the old menu. up/down arrows choose previous/next menu-item.

---

### Post by bean123 on 2010-01-12
> **McDuff said:**
> no problem with the old menu. up/down arrows choose previous/next menu-item.

Copy widget.mod from attachment to /boot/grub/, and see if it fixes this issue. (Don't run grub-install, otherwise it'd overwrite files in /boot/grub).

---

### Post by McDuff on 2010-01-12
> **bean123 said:**
> Copy widget.mod from attachment to /boot/grub/, and see if it fixes this issue. (Don't run grub-install, otherwise it'd overwrite files in /boot/grub).

this fixed the issue. what does widget.mod do? had i missed it somewhere?

---

### Post by bean123 on 2010-01-12
> **McDuff said:**
> this fixed the issue. what does widget.mod do? had i missed it somewhere?

Oh nice. I've changed the handling of key query. Previously, it sleep some time between testing key press, maybe some key got lost in the process. Now it just keep polling. BTW, the progressbar should be smoother using this method, although cpu usage would be higher during the timeout period.

---

### Post by bean123 on 2010-01-12
Just upload a new pacakge 1.97+burg.20100112-2~ppa6 (karmic and lucid) that contains the read key fix.

---

### Post by McDuff on 2010-01-12
thank you!

---

### Post by Netich on 2010-01-16
This thread is too silent!

Im loving the folding option. Im trying to change the background to match the xplash one. What file of the theme do i have to modify?

---

### Post by vishalrao on 2010-01-16
BURG ppa safe to use with lucid A2 latest stuff? :)

---

### Post by Netich on 2010-01-16
I changed the background and im trying to customize the theme, but i have trouble undertanding these lines. I cant find any documentation about BURG.

```
top_left = ",,#000000/cyan/blue,#0x250F:,,#000000/light-gray/blue,#0x2554"
```

---

### Post by bean123 on 2010-01-17
> **vishalrao said:**
> BURG ppa safe to use with lucid A2 latest stuff? :)

Yeah, it should work.

---

### Post by bean123 on 2010-01-17
> **Netich said:**
> This thread is too silent!

Im loving the folding option. Im trying to change the background to match the xplash one. What file of the theme do i have to modify?

Modify /boot/grub/themes/refit/theme.txt.

To change background image, find this:

```

class {
  screen {
    background = ",,#BFBFBF/blue"
  }
  ...
}

```

And change it to:
```

class {
  screen {
    background = "${theme_dir}/splash.png,,#BFBFBF/blue"
  }
  ...
}

```

You also need to copy splash.png to /boot/grub/themes/refit directory.

---

### Post by bean123 on 2010-01-17
> **Netich said:**
> I changed the background and im trying to customize the theme, but i have trouble undertanding these lines. I cant find any documentation about BURG.

```
top_left = ",,#000000/cyan/blue,#0x250F:,,#000000/light-gray/blue,#0x2554"
```

Here is the document:

[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

A panel has eight border image, top_left is the top left corner. This attribute is split into two parts, ",,#000000/cyan/blue,#0x250F" is for normal state, ",,#000000/light-gray/blue,#0x2554" is for selected state, #0x250F and #0x2554 is the unicode for single and double box char. and #000000/cyan/blue and #000000/light-gray/blue are color. It means use #000000 (black) in graphic mode, cyan/blue in text mode.

---

### Post by Starks on 2010-01-17
> **bean123 said:**
> Yeah, it should work.
It should. But it doesn't.

> E: /var/cache/apt/archives/grub-pc_1.98+burg.20100114-1~ppa6+lucid_i386.deb: trying to overwrite '/usr/bin/grub-mkrescue', which is also in package grub-common 0I've had to get around this bug for weeks by purging grub-common first.

Also, is folding only for refit?

---

### Post by bean123 on 2010-01-17
> **Starks said:**
> It should. But it doesn't.

I've had to get around this bug for weeks by purging grub-common first.

This is caused by different packing method. BURG put grub-mkresuce in grub-pc, and GRUB put it in grub-common, so when upgrade from grub to burg, it would find conflicts. Anyway, I can move grub-mkresuce to grub-common in the next version.

> Also, is folding only for refit?

Other theme can use folding as well, but some function is missing, like F7 hotkey to expand the full list. I will update them soon to have full folding support.

---

### Post by _AstraL_ on 2010-01-17
BURG is really cool for me, but I have one problem left. It was discussed two or three pages back, but no one fixed it though. That's what I get with Sora (see attachment)
**UPD**: solved (yay!) by removing theme configs from /etc/grub.d/40_custom

---

### Post by cecilpierce on 2010-01-17
is BURG about the sane as 1.98~experimental.20100111.1-1 from debian ?
was wondering about horizontal lines when booting.
i had some problems with BURG so im trying the 1.98 experimental. thanks.

---

### Post by libihero on 2010-01-17
i followed the directions for burg and all i get is something similiar to the old GRUB, except the box where the operating systems are is blue

---

### Post by MacUntu on 2010-01-17
Can't I have a custom font AND a custom background with GRUB2? I can only get either one to work.

---

### Post by bean123 on 2010-01-17
> **cecilpierce said:**
> is BURG about the sane as 1.98~experimental.20100111.1-1 from debian ?
was wondering about horizontal lines when booting.
i had some problems with BURG so im trying the 1.98 experimental. thanks.

No, they're not the same, config file format are different. You can't use the menu config from grub experiment in BURG.

---

### Post by bean123 on 2010-01-26
New package: 1.98+20100126-1

It changes file prefix to burg, so it can coexist with grub2.  For example:

grub-install => burg-install
update-grub => update-burg
/boot/grub/grub.cfg => /boot/burg/burg.cfg
/etc/grub.d => /etc/burg.d
/etc/default/grub => /etc/default/burg

New feature for this version:

* New command ntldr and freedos, support loading of ntldr/grldr/bootmgr/kernel.sys directly.
* You can use q hotkey to go back to old grub menu.
* All themes support folding, although the popup list of sora doesn't look very good.

Here is the installation step for the new package:

1. Install program and themes
```

sudo apt-get install burg burg-themes

```

2. Use burg-install to install the new boot loader to MBR/BS.

2. Edit /etc/default/burg, uncomment the GRUB_THEME setting, you can also uncomment GRUB_FOLD to fold items.

3. Use update-burg to generate config file /boot/burg/burg.cfg

4. (Optional) Install burg-emu for live preview.

---

### Post by cecilpierce on 2010-01-26
When I installed new burg it says,
Suggested packages:
  multiboot-doc burg-emu, but multiboot-doc not available ???

---

### Post by cecilpierce on 2010-01-26
When I run burg-emu it says "no suitable modes found" and I get this:
if I hit q it goes to text menu, how can I fix this ?
Thanks, Cecil

---

### Post by Starks on 2010-01-26
New burg packages don't detect memtest or dell linux recovery.

---

### Post by bean123 on 2010-01-26
> **Starks said:**
> New burg packages don't detect memtest or dell linux recovery.

BURG uses directory /etc/burg.d to store scripts. To enable memtest, copy 20_memtest86+ from /etc/grub.d to /etc/burg.d and run update-burg.

---

### Post by bean123 on 2010-01-27
> **cecilpierce said:**
> When I installed new burg it says,
Suggested packages:
  multiboot-doc burg-emu, but multiboot-doc not available ???

I copy this verbatim from grub2, it'd be removed in the next version.

> **cecilpierce said:**
> When I run burg-emu it says "no suitable modes found" and I get this:
if I hit q it goes to text menu, how can I fix this ?
Thanks, Cecil

Oh sorry, I forget to add the libsdl1.2-dev as source dependence so burg-emu don't support graphic mode ! This will be fixed in the next ppa package.

---

### Post by bean123 on 2010-01-27
New version 1.98+20100127-1:

* Fix the preview burg-emu problem
* Add new command msdos which can be used to chainload io.sys of win98/winme, for example:

set root=(hd0,1)
msdos /io.sys
boot

---

### Post by cecilpierce on 2010-01-27
> **bean123 said:**
> New version 1.98+20100127-1:

* Fix the preview burg-emu problem
* Add new command msdos which can be used to chainload io.sys of win98/winme, for example:

set root=(hd0,1)
msdos /io.sys
boot

Thanks bean123, just got it, works great. Are there any new themes around ?

---

### Post by Starks on 2010-01-27
> **bean123 said:**
> BURG uses directory /etc/burg.d to store scripts. To enable memtest, copy 20_memtest86+ from /etc/grub.d to /etc/burg.d and run update-burg.
Thanks.

---

### Post by Starks on 2010-01-27
Hmmm. Plymouth doesn't want to work after setting burg to take over grub.

"unexpectedly disconnected from boot status daemon"

This wasn't a problem before the prefix change.

---

### Post by ranch hand on 2010-01-27
> **Starks said:**
> Hmmm. Plymouth doesn't want to work after setting burg to take over grub.

"unexpectedly disconnected from boot status daemon"

This wasn't a problem before the prefix change.
I thought that message may be about bootchart.  I do have plymouth (not working on this OS but I am just running grub1.98.  I have that message.  I just about had to change my pants the first time it came up.

---

### Post by djg5211 on 2010-01-28
Hi All...:D

 I have been using the Grub2/Burg setup on my Lucid for a few days
now and i have most of it figured out and it works quite well for
me, BUT, i have ONE question...

I have googled the subject in every way i can think of and NONE
of the posts that i have found have given a solution.

QUESTION:
Does anyone know how to change the TEXT FONT SIZE on the menu?
I am actually using the ubuntu theme in my Grub2/Burg and in
theme.txt (as well as some of the other files) there are lines
like ->   font = "Fixed Bold 16" but nothing i try changes
anything. Before anyone asks.... YES i always do 'sudo update-grub'
after i modify ANYTHING.

I have seen this question several times regarding the font size
but it seems like each time a post mentioned this there were
other questions included and the thread always strayed off in a 
different direction and the font issue is never addressed.
I am sure it is a very simple modification it's just a matter
of what to modify.

Other than this font issue i really like this Grub2/Burg thing!
I agree with some of the posts that i read that made reference
to SUSE (and other distros) about the Grub menu thing and how
it's overdue in Ubuntu but i didn't really want to install
SUSE (or whatever) just to get a cool graphical boot menu.

Thanks in advance for any help!

Dave:biggrin:

---

### Post by vishalrao on 2010-01-28
If you don't find a proper solution one alternative to try would be to set the gfxmode to a lower resolution and set gfxpayload to your higher previous gfxmode resolution instead of "keep", so i mean:

instead of :

```

set gfxmode=1920x1200
set gfxpayload=keep

```

make it:

```

set gfxmode=1024x768
set gfxpayload=1920x1200

```

would that work? if it does, the fonts should be larger but not as smooth due to lower res.

---

### Post by djg5211 on 2010-01-28
> **vishalrao said:**
> If you don't find a proper solution one alternative to try would be to set the gfxmode to a lower resolution and set gfxpayload to your higher previous gfxmode resolution instead of "keep", so i mean:

instead of :

```

set gfxmode=1920x1200
set gfxpayload=keep

```

make it:

```

set gfxmode=1024x768
set gfxpayload=1920x1200

```

would that work? if it does, the fonts should be larger but not as smooth due to lower res.

Vishalrao,

I appreciate your quick reply. Uh, it sounds to me like that would
work but WHICH FILE are we talking about making the changes in?
I have skimmed through so many of them i lost track of what is what!
I'm sortof assuming that eventually maybe someone will write a
special config editor or combine things into less config files!!!!
(Hey..... Wishful thinking... Tee Hee!) 

Thanks Again!
Dave

---

### Post by Starks on 2010-01-28
gfxmode and gfxpayload can't exceed the maximum vbe resolution supported by my pc, right?

---

### Post by vishalrao on 2010-01-28
which file? i believe for gfxmode you set some var called "GRUB_GFXMODE" in /etc/defaults/grub. for gfxpayload you have to add the line "set gfxpayload=xxxxxx" to the 00_header script under the line that sets "set gfxmode=GRUB_GFXMODE". then run update-grub.

max vbe resolution? yes i think you need to ensure you pick a supported resolution else it will drop to default low-res. for example, it looks like grub's framebuffer module is better than the vesafb kernel module because grub can do my native lcd 1920x1200 but kernel/console seems to only work mostly at 1024x768 ...

---

### Post by bean123 on 2010-01-29
> **djg5211 said:**
> Hi All...:D

 I have been using the Grub2/Burg setup on my Lucid for a few days
now and i have most of it figured out and it works quite well for
me, BUT, i have ONE question...

I have googled the subject in every way i can think of and NONE
of the posts that i have found have given a solution.

QUESTION:
Does anyone know how to change the TEXT FONT SIZE on the menu?
I am actually using the ubuntu theme in my Grub2/Burg and in
theme.txt (as well as some of the other files) there are lines
like ->   font = "Fixed Bold 16" but nothing i try changes
anything. Before anyone asks.... YES i always do 'sudo update-grub'
after i modify ANYTHING.

I have seen this question several times regarding the font size
but it seems like each time a post mentioned this there were
other questions included and the thread always strayed off in a 
different direction and the font issue is never addressed.
I am sure it is a very simple modification it's just a matter
of what to modify.

Other than this font issue i really like this Grub2/Burg thing!
I agree with some of the posts that i read that made reference
to SUSE (and other distros) about the Grub menu thing and how
it's overdue in Ubuntu but i didn't really want to install
SUSE (or whatever) just to get a cool graphical boot menu.

Thanks in advance for any help!

Dave:biggrin:

First you need to open /boot/burg/fonts/font.lst to see what fonts are available, then you can replace the font parameter, for example "Fixed Regular 20".

You can use burg-mkfont to generate new fonts, -h option to show all options, for example:

```

burg-mkfont -o my_font.pf2 -s 20 my_font.bdf

```

You can also convert TTF.

Then, copy my_font.pf2 to /boot/burg/fonts, and use the following command to update the font list:

```

cd /boot/burg/fonts
sudo burg-mkfont -i *.pf2 > font.lst

```

---

### Post by djg5211 on 2010-01-29
> **bean123 said:**
> First you need to open /boot/burg/fonts/font.lst to see what fonts are available, then you can replace the font parameter, for example "Fixed Regular 20".

You can use burg-mkfont to generate new fonts, -h option to show all options, for example:

```

burg-mkfont -o my_font.pf2 -s 20 my_font.bdf

```

You can also convert TTF.

Then, copy my_font.pf2 to /boot/burg/fonts, and use the following command to update the font list:

```

cd /boot/burg/fonts
sudo burg-mkfont -i *.pf2 > font.lst

```

Hey thanks Bean123!!!! I copied all of this down and will
hermetically seal it in a mayonaise jar and lock it away
in a safe so i don't lose it. I did do the method mentioned
in the previous post and it worked okay as for making the font
bigger but as also mentioned it did make the letters somewhat
grainy looking. I'll try to follow your instructions and see
what happens....... and, i say 'see what happens' because
i know me.... heh heh...

Thanks for all of the help guys! I'll pop back by after i
impliment this and let you know the outcome.

Cheers!
Dave

---

### Post by bean123 on 2010-01-29
New version burg - 1.98+20100129-1:

Password integration. You can now configure password using GRUB_USERS variable in /etc/default/burg, and update-burg would generate the correct setting automatically. For more information:

[http://code.google.com/p/burg/wiki/Authentication](http://code.google.com/p/burg/wiki/Authentication)

---

### Post by drs305 on 2010-01-29
> **bean123 said:**
> New version burg - 1.98+20100129-1:

Password integration. You can now configure password using GRUB_USERS variable in /etc/default/burg, and update-burg would generate the correct setting automatically. For more information:

[http://code.google.com/p/burg/wiki/Authentication](http://code.google.com/p/burg/wiki/Authentication)

Bean123, 

Is this capability now in Grub 2 as well?

I appreciate all that you have done on BURG. 

Is it time to start a new thread devoted specifically to BURG to make the distinction between your work and the 'official' Grub product? I know your posts have been in response to users' questions and really appreciate the time you are taking to help everyone interested in theming. 

I am not trying to hijack this thread to make it a BURG v Grub discussion. :-)

---

### Post by cecilpierce on 2010-01-29
I like the winter theme, is there any way to get icons for the OS,s like in sora ?

---

### Post by bean123 on 2010-01-29
> **drs305 said:**
> Bean123, 

Is this capability now in Grub 2 as well?

I appreciate all that you have done on BURG. 

Is it time to start a new thread devoted specifically to BURG to make the distinction between your work and the 'official' Grub product? I know your posts have been in response to users' questions and really appreciate the time you are taking to help everyone interested in theming. 

I am not trying to hijack this thread to make it a BURG v Grub discussion. :-)

grub2 has the infrastructure for password support, but you need to edit grub.cfg manually:

[http://grub.enbug.org/Authentication](http://grub.enbug.org/Authentication)

Also, the new menu system will popup a dialog for username and password, but grub2 just clear the screen and print the prompt.

---

### Post by bean123 on 2010-01-29
> **cecilpierce said:**
> I like the winter theme, is there any way to get icons for the OS,s like in sora ?

Sure, you can edit /boot/burg/themes/winter/theme.txt, add these inside the class section, for example:

```

class {
  ...
  Windows {
    image = "${theme_dir}/os_win.png"
  }

  Ubuntu {
    image = "${theme_dir}/os_ubuntu.png"
  }

  image {
    image = "${theme_dir}/os_unknown.png"
  }
}

```

And copy icons to /boot/burg/themes/winter/.

---

### Post by drs305 on 2010-01-29
> **bean123 said:**
> grub2 has the infrastructure for password support, but you need to edit grub.cfg manually:

[http://grub.enbug.org/Authentication](http://grub.enbug.org/Authentication)

Also, the new menu system will popup a dialog for username and password, but grub2 just clear the screen and print the prompt.

Currently in Grub 2 you set the usernames/passwords in /etc/grub.d/00_header and it will prompt for username/password if a password-protected entry is selected or the user tries to edit the menu. It's still not encrypted, at least in 1.97 beta.

But the GRUB_USERS feature you now have is a new feature to me and a good addition. 

Now back to theming ...

---

### Post by bean123 on 2010-01-29
> **drs305 said:**
> Currently in Grub 2 you set the usernames/passwords in /etc/grub.d/00_header and it will prompt for username/password if a password-protected entry is selected or the user tries to edit the menu. It's still not encrypted, at least in 1.97 beta.

It uses pbkdf2 encryption for password. This function has been merged into grub2 trunk lately, and it's used in BURG as well. The hashed password is stored in /etc/default/burg-passwd.

---

### Post by richlyn9 on 2010-01-30
after going through many posts,threads and blogs i followed the post [here]("http://ubuntuforums.org/showpost.php?p=8623952&postcount=47") to install burg and get a theme  in grub

I have a lucid,karmic and windows XP multi boot
i wanted to install it on a dedicated grub partition but decided to try theming first and then install it on a 1 gb partition


heres what i folowed according to the post

richlyn@richlyn-lucid:~$ sudo apt-get install grub-pc 
[sudo] password for richlyn: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
grub-pc is already the newest version. 
grub-pc set to manually installed. 
The following packages were automatically installed and are no longer required: 
  linux-headers-2.6.32-10-generic linux-headers-2.6.32-10 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 156 not upgraded. 
richlyn@richlyn-lucid:~$ sudo grub-install "(hd0)" 
Installation finished. No error reported. 
richlyn@richlyn-lucid:~$ cd /boot/grub 
richlyn@richlyn-lucid:/boot/grub$ sudo unzip ~/theme_fonts.zip 
Archive:  /home/richlyn/theme_fonts.zip 
   creating: fonts/ 
  inflating: fonts/10x20.pf2         
  inflating: fonts/4x6.pf2           
  inflating: fonts/5x7.pf2           
  inflating: fonts/5x8.pf2           
  inflating: fonts/6x10.pf2          
  inflating: fonts/6x12.pf2          
  inflating: fonts/6x13.pf2          
  inflating: fonts/6x13B.pf2         
  inflating: fonts/6x13O.pf2         
  inflating: fonts/6x9.pf2           
  inflating: fonts/7x13.pf2          
  inflating: fonts/7x13B.pf2         
  inflating: fonts/7x13O.pf2         
  inflating: fonts/7x14.pf2          
  inflating: fonts/7x14B.pf2         
  inflating: fonts/8x13.pf2          
  inflating: fonts/8x13B.pf2         
  inflating: fonts/8x13O.pf2         
  inflating: fonts/9x15.pf2          
  inflating: fonts/9x15B.pf2         
  inflating: fonts/9x18.pf2          
  inflating: fonts/9x18B.pf2         
  inflating: fonts/anorexia.pf2      
  inflating: fonts/aqui.pf2          
  inflating: fonts/ascii.pf2         
  inflating: fonts/clR6x12.pf2       
  inflating: fonts/cure.pf2          
  inflating: fonts/drift.pf2         
  inflating: fonts/edges.pf2         
  inflating: fonts/fkp.pf2           
  inflating: fonts/font.lst          
  inflating: fonts/gelly.pf2         
  inflating: fonts/glisp-bold.pf2    
  inflating: fonts/glisp.pf2         
  inflating: fonts/Helvetica-10.pf2  
  inflating: fonts/Helvetica-12.pf2  
  inflating: fonts/Helvetica-14.pf2  
  inflating: fonts/Helvetica-18.pf2  
  inflating: fonts/Helvetica-24.pf2  
  inflating: fonts/Helvetica-8.pf2   
  inflating: fonts/Helvetica-Bold-10.pf2  
  inflating: fonts/Helvetica-Bold-12.pf2  
  inflating: fonts/Helvetica-Bold-14.pf2  
  inflating: fonts/Helvetica-Bold-18.pf2  
  inflating: fonts/Helvetica-Bold-24.pf2  
  inflating: fonts/Helvetica-Bold-8.pf2  
  inflating: fonts/kates.pf2         
  inflating: fonts/lime.pf2          
  inflating: fonts/mints-mild.pf2    
  inflating: fonts/mints-strong.pf2  
  inflating: fonts/New_Century_Schoolbook-10.pf2  
  inflating: fonts/New_Century_Schoolbook-12.pf2  
  inflating: fonts/New_Century_Schoolbook-14.pf2  
  inflating: fonts/New_Century_Schoolbook-18.pf2  
  inflating: fonts/New_Century_Schoolbook-24.pf2  
  inflating: fonts/New_Century_Schoolbook-8.pf2  
  inflating: fonts/New_Century_Schoolbook-Bold-10.pf2  
  inflating: fonts/New_Century_Schoolbook-Bold-12.pf2  
  inflating: fonts/New_Century_Schoolbook-Bold-14.pf2  
  inflating: fonts/New_Century_Schoolbook-Bold-18.pf2  
  inflating: fonts/New_Century_Schoolbook-Bold-24.pf2  
  inflating: fonts/New_Century_Schoolbook-Bold-8.pf2  
  inflating: fonts/nu.pf2            
  inflating: fonts/smoothansi.pf2    
  inflating: fonts/snap.pf2          
  inflating: fonts/unifont.pf2       
richlyn@richlyn-lucid:/boot/grub$ sudo unzip ~/theme_ubuntu.zip 
Archive:  /home/richlyn/theme_ubuntu.zip 
   creating: themes/ubuntu/ 
 extracting: themes/ubuntu/config.lst  
  inflating: themes/ubuntu/desktop.png  
 extracting: themes/ubuntu/progress_bar_c.png  
 extracting: themes/ubuntu/progress_highlight_c.png  
  inflating: themes/ubuntu/terminal_c.png  
  inflating: themes/ubuntu/terminal_e.png  
  inflating: themes/ubuntu/terminal_n.png  
 extracting: themes/ubuntu/terminal_ne.png  
 extracting: themes/ubuntu/terminal_nw.png  
  inflating: themes/ubuntu/terminal_s.png  
 extracting: themes/ubuntu/terminal_se.png  
 extracting: themes/ubuntu/terminal_sw.png  
  inflating: themes/ubuntu/terminal_w.png  
  inflating: themes/ubuntu/theme.txt  
richlyn@richlyn-lucid:/boot/grub$ sudo unzip ~/theme_sora.zip 
Archive:  /home/richlyn/theme_sora.zip 
   creating: themes/sora/ 
  inflating: themes/sora/background.png  
   creating: themes/sora/clean/ 
  inflating: themes/sora/clean/clean.txt  
  inflating: themes/sora/clean/config.lst  
  inflating: themes/sora/clean/theme.cfg  
  inflating: themes/sora/config.lst  
   creating: themes/sora/extended/ 
  inflating: themes/sora/extended/config.lst  
  inflating: themes/sora/extended/extended.txt  
  inflating: themes/sora/extended/theme.cfg  
   creating: themes/sora/icons/ 
  inflating: themes/sora/icons/button-linux-hover.png  
  inflating: themes/sora/icons/button-linux.png  
 extracting: themes/sora/icons/button-osx-hover.png  
 extracting: themes/sora/icons/button-osx.png  
 extracting: themes/sora/icons/button-ubuntu-hover.png  
 extracting: themes/sora/icons/button-ubuntu.png  
 extracting: themes/sora/icons/button-unknown-hover.png  
  inflating: themes/sora/icons/button-unknown.png  
 extracting: themes/sora/icons/button-windows-hover.png  
  inflating: themes/sora/icons/button-windows.png  
  inflating: themes/sora/icons/icons.txt  
   creating: themes/sora/icons-nopop/ 
 extracting: themes/sora/icons-nopop/button-linux-hover.png  
  inflating: themes/sora/icons-nopop/button-linux.png  
 extracting: themes/sora/icons-nopop/button-osx-hover.png  
 extracting: themes/sora/icons-nopop/button-osx.png  
 extracting: themes/sora/icons-nopop/button-ubuntu-hover.png  
 extracting: themes/sora/icons-nopop/button-ubuntu.png  
 extracting: themes/sora/icons-nopop/button-unknown-hover.png  
 extracting: themes/sora/icons-nopop/button-unknown.png  
 extracting: themes/sora/icons-nopop/button-windows-hover.png  
  inflating: themes/sora/icons-nopop/button-windows.png  
  inflating: themes/sora/icons-nopop/icons.txt  
   creating: themes/sora/images/ 
  inflating: themes/sora/images/000-70opaque.png  
  inflating: themes/sora/images/button-bg.png  
  inflating: themes/sora/images/button-hover-bg.png  
 extracting: themes/sora/images/button-hover-l.png  
 extracting: themes/sora/images/button-hover-r.png  
 extracting: themes/sora/images/button-l.png  
 extracting: themes/sora/images/button-r.png  
 extracting: themes/sora/images/button-tools-hover.png  
 extracting: themes/sora/images/button-tools.png  
  inflating: themes/sora/images/container-b.png  
  inflating: themes/sora/images/container-bg.png  
 extracting: themes/sora/images/container-bl.png  
 extracting: themes/sora/images/container-br.png  
  inflating: themes/sora/images/container-l.png  
 extracting: themes/sora/images/container-r.png  
  inflating: themes/sora/images/container-title-bg.png  
  inflating: themes/sora/images/container-title-l.png  
  inflating: themes/sora/images/container-title-r.png  
  inflating: themes/sora/images/container-title-t.png  
 extracting: themes/sora/images/container-title-tl.png  
 extracting: themes/sora/images/container-title-tr.png  
  inflating: themes/sora/images/dialog-b.png  
  inflating: themes/sora/images/dialog-bg.png  
 extracting: themes/sora/images/dialog-bl.png  
 extracting: themes/sora/images/dialog-br.png  
  inflating: themes/sora/images/dialog-lr.png  
  inflating: themes/sora/images/dialog-spacer.png  
  inflating: themes/sora/images/dialog-t.png  
 extracting: themes/sora/images/dialog-tl.png  
 extracting: themes/sora/images/dialog-tr.png  
  inflating: themes/sora/images/progressbar-bg-b.png  
 extracting: themes/sora/images/progressbar-bg-bl.png  
 extracting: themes/sora/images/progressbar-bg-br.png  
 extracting: themes/sora/images/progressbar-bg-l.png  
 extracting: themes/sora/images/progressbar-bg-r.png  
  inflating: themes/sora/images/progressbar-bg-t.png  
  inflating: themes/sora/images/progressbar-bg-tl.png  
  inflating: themes/sora/images/progressbar-bg-tr.png  
  inflating: themes/sora/images/progressbar-bg.png  
 extracting: themes/sora/images/text-line-l.png  
 extracting: themes/sora/images/text-line-r.png  
 extracting: themes/sora/images/txt-about.png  
 extracting: themes/sora/images/txt-help.png  
 extracting: themes/sora/images/txt-select.png  
 extracting: themes/sora/images/txt-tools.png  
  inflating: themes/sora/menus.txt   
  inflating: themes/sora/style.txt   
  inflating: themes/sora/theme.cfg   
  inflating: themes/sora/theme.txt   
richlyn@richlyn-lucid:/boot/grub$ sudo gedit /etc/default/grub 
richlyn@richlyn-lucid:/boot/grub$ sudo unzip ~/theme_refit.zip 
Archive:  /home/richlyn/theme_refit.zip 
   creating: themes/refit/ 
  inflating: themes/refit/box_r.png  
 extracting: themes/refit/config.lst  
 extracting: themes/refit/os_debian.png  
 extracting: themes/refit/os_ubuntu.png  
  inflating: themes/refit/box_l.png  
 extracting: themes/refit/os_freebsd.png  
  inflating: themes/refit/box_b.png  
  inflating: themes/refit/box_t.png  
 extracting: themes/refit/box_tr.png  
 extracting: themes/refit/box_br.png  
 extracting: themes/refit/box_bl.png  
  inflating: themes/refit/os_win.png  
 extracting: themes/refit/os_linux.png  
 extracting: themes/refit/box_tl.png  
  inflating: themes/refit/os_suse.png  
 extracting: themes/refit/os_osx.png  
  inflating: themes/refit/theme.txt  
  inflating: themes/refit/os_unknown.png  
richlyn@richlyn-lucid:/boot/grub$ sudo update-grub 
Generating grub.cfg ... 
Found linux image: /boot/vmlinuz-2.6.32-11-generic 
Found initrd image: /boot/initrd.img-2.6.32-11-generic 
Found linux image: /boot/vmlinuz-2.6.32-10-generic 
Found initrd image: /boot/initrd.img-2.6.32-10-generic 
Found memtest86+ image: /boot/memtest86+.bin 
Found Microsoft Windows XP Professional on /dev/sda1 
Found Ubuntu 9.10 (9.10) on /dev/sda9 
done 
richlyn@richlyn-lucid:/boot/grub$ 



i stll dont get the desired result


heres what the grub config contains

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_THEME=sora
GRUB_GFXMODE=1024x768
#GRUB_FOLD=1
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"



[COLOR="Black"][COLOR="Navy"]**Where have i gone wrong or what else do i need to do???**[/COLOR][/COLOR]

---

### Post by Starks on 2010-01-30
You followed outdated directions and I hope vish updates the first post to reflect this.

[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)

Installing BURG now is a cakewalk compared to what it used to be.

---

### Post by ranch hand on 2010-01-30
OK, you buggers got me.  I installed burg on a 9.10 install here on the test platform during my morning chroot update of all installs.

I have to do a little more studying in the files to see what I expect and then try it out.

---

### Post by richlyn9 on 2010-01-30
alright i will re do everyhing according to the updates and let you know...

---

### Post by ranch hand on 2010-01-30
Well, that was interesting.

Keep in mind that I have 9 OS' on the test platform.  Five versions of Ubuntu 10.04.  One 9.10 minimal upgraded to 10.04 using the Gnome DE.  One Lubuntu 10.04.  One Zenix 9.10.   One Stoner Edition 1.2 (9.10 respin).  One Mandrva 2009-1.  One Ubuntu 8.04.

My initial boot through burg was bad.  I am using the default theme (refit).  All I got was a blue screen with a couple of boxes in the center and a progress bar.  I hit enter and booted to Stoner (default as this is where burg is installed).

Added my custom file to burg.d and updated burg.  Rebooted.  Now I have 4 large circular ? incons in a horizontal row.  The one on the left takes me to Stoner.  The next takes me to Lounge Lizard which is next on the custom menu.

I did not explore further as the pattern was fairly clear.  Booted to Lounge, chrooted to Stoned Lizard and reinstalled that grub on the MBR and here I am back with boinc running to beat the band.

Now, what on earth am I doing wrong, if anything?  Do I need to change something so I have a usable menu?  Am I in the wrong theme?

The only editing that I did was to enable the themes and make the time out 100 instead of 5 (thank god I did that or the first boot would have been ugly).

Waiting with bated breath for words of wisdom.

---

### Post by richlyn9 on 2010-01-30
the issues [page]("http://code.google.com/p/burg/issues/list") for burg lists an issue with sora theme.....just updating automatically will get the latest updates and fixes i believe. or has one to manuallly get the updates?

---

### Post by richlyn9 on 2010-01-30
just finished installing burg according the latest.....waiting to test with fingers crossed!

BTY how and where do  use the hot-keys defined for the themes?

---

### Post by richlyn9 on 2010-01-30
Wwoohhhhoooooooo
successfully installed burg and its now perfectly running....

theres one point though..
since i have two ubuntu distros it dosent say which is which.
guess i will have to try a differrent theme or edit a few file within?

okay..now for some advanced options
hope i do the right moves...

---

### Post by bean123 on 2010-01-30
> **ranch hand said:**
> Well, that was interesting.

Keep in mind that I have 9 OS' on the test platform.  Five versions of Ubuntu 10.04.  One 9.10 minimal upgraded to 10.04 using the Gnome DE.  One Lubuntu 10.04.  One Zenix 9.10.   One Stoner Edition 1.2 (9.10 respin).  One Mandrva 2009-1.  One Ubuntu 8.04.

My initial boot through burg was bad.  I am using the default theme (refit).  All I got was a blue screen with a couple of boxes in the center and a progress bar.  I hit enter and booted to Stoner (default as this is where burg is installed).

Added my custom file to burg.d and updated burg.  Rebooted.  Now I have 4 large circular ? incons in a horizontal row.  The one on the left takes me to Stoner.  The next takes me to Lounge Lizard which is next on the custom menu.

I did not explore further as the pattern was fairly clear.  Booted to Lounge, chrooted to Stoned Lizard and reinstalled that grub on the MBR and here I am back with boinc running to beat the band.

Now, what on earth am I doing wrong, if anything?  Do I need to change something so I have a usable menu?  Am I in the wrong theme?

The only editing that I did was to enable the themes and make the time out 100 instead of 5 (thank god I did that or the first boot would have been ugly).

Waiting with bated breath for words of wisdom.

Currently, refit only has icon for ubuntu, debian, suse, freebsd, osx and windows, for other os, it shows the default question mark icon. In such case, you can add the icons for missing OS, or just use theme like ubuntu that display text instead of icon.

---

### Post by vishalrao on 2010-01-30
@starks: thanks, i've added that link to the first post.

---

### Post by ranch hand on 2010-01-30
> **bean123 said:**
> Currently, refit only has icon for ubuntu, debian, suse, freebsd, osx and windows, for other os, it shows the default question mark icon. In such case, you can add the icons for missing OS, or just use theme like ubuntu that display text instead of icon.
OK, I saw that in the file for the theme.

What I do not understand is that I have 6 OS' running an Ubuntu kernel.  I could see the problem with the 5 Ubuntu 10.04 installs seeing that burg is on Stoner Edition1.2.  Stoner Edition1.2 is a 9.10 respin.

Grub-legacy and grub2 both see it as Ubuntu running the 2.6.31 kernel.  The main difference is in the default apps added to the normal Ubuntu mix.  Burg does not appear to see it that way.

There is also the matter of only 4 icons for all the installs on the drive.   I did not enable "folding" so that all would be on there.

I did change the theme to "ubuntu" for the text menu and put in a custom bg (I have a custom bg for each of my grub2 installs so that I can see which one I am using when it comes up).  That seems to work very well.

I also have to look into the password protection.  I am getting a laptop for my wife (System76) and she will take it to shows (Silversmith).  I want the files encrypted and the boot menu protected.  I thought things were getting interesting enough with burg to enjoy playing with it and it does, I hear, support these things pretty well.

Thought I would try it out on here before the laptop gets here (Monday?).

The theme problem should not be a problem there as there is only 9.10 on the bugger.  320Gb HDD and only one OS, tough for me to handle.

I will try "folding" on a different them on here to see what that does.  If it is like the others I have seen I won't be using it as it gets on my thungas.  There is no need for that extra click and I want to see my menu all the time.  But I may as well try it.  Besides that, I was wondering if the icon probem had to do with my video card.  A lot of things do not work well with it.  Those icons looked pretty big (inch dia or around there).

---

### Post by bean123 on 2010-01-31
> **ranch hand said:**
> OK, I saw that in the file for the theme.

What I do not understand is that I have 6 OS' running an Ubuntu kernel.  I could see the problem with the 5 Ubuntu 10.04 installs seeing that burg is on Stoner Edition1.2.  Stoner Edition1.2 is a 9.10 respin.

Grub-legacy and grub2 both see it as Ubuntu running the 2.6.31 kernel.  The main difference is in the default apps added to the normal Ubuntu mix.  Burg does not appear to see it that way.

BURG relies on os-prober to detect OS name, perhaps you can check the generated burg.cfg and see what's the value of --class option for this OS.

> 
There is also the matter of only 4 icons for all the installs on the drive.   I did not enable "folding" so that all would be on there.

It's possible that the other icons are located outside the screen, you can use a large resolution like 1024x768 and see if it shows extra icon.

> 
I will try "folding" on a different them on here to see what that does.  If it is like the others I have seen I won't be using it as it gets on my thungas.  There is no need for that extra click and I want to see my menu all the time.  But I may as well try it.  Besides that, I was wondering if the icon probem had to do with my video card.  A lot of things do not work well with it.  

You can try burg-emu and see if it has the same issue. burg-emu runs in host OS and is not affected by physical video card.

> Those icons looked pretty big (inch dia or around there).
Change screen resolution using GRUB_GFXMODE.

---

### Post by richlyn9 on 2010-01-31
After sucessfully installing burg i am now trying to install it on a dedicated partition.
i have made a 1 GB partition hd0,11 and have formatted it to ext3 which has a label Burg
my command  goes 
*sudo burg-install –root-directory=/media/Burg /dev/sda*

i get the folllowing
[COLOR="Blue"]richlyn@richlyn-personal:~$ sudo burg-install –root-directory=/media/Burg /dev/sda[sudo] password for richlyn: 
More than one install_devices?
Usage: burg-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --burg-setup=FILE       use FILE as burg-setup
  --burg-mkimage=FILE     use FILE as burg-mkimage
  --burg-mkdevicemap=FILE use FILE as burg-mkdevicemap
  --burg-probe=FILE       use FILE as burg-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --alt                   alternative setup mode
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a BURG device name or a system device filename.

burg-install copies BURG images into /boot/burg (or /burg on NetBSD and
OpenBSD), and uses burg-setup to install grub into the boot sector.

If the --root-directory option is used, then burg-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bean123ch@gmail.com>.
richlyn@richlyn-personal:~$[/COLOR] 



**What have i missed?**

---

### Post by bean123 on 2010-01-31
> **richlyn9 said:**
> After sucessfully installing burg i am now trying to install it on a dedicated partition.
i have made a 1 GB partition hd0,11 and have formatted it to ext3 which has a label Burg
my command  goes 
*sudo burg-install &#8211;root-directory=/media/Burg /dev/sda*

The option should be --root-directory. Also, /dev/sda means MBR, to install to dedicated partition (hd0,11), use something like this:

```

sudo burg-install --force -&#8211;root-directory=/media/Burg /dev/sda11

```

---

### Post by Starks on 2010-01-31
> **richlyn9 said:**
> Wwoohhhhoooooooo
successfully installed burg and its now perfectly running....

theres one point though..
since i have two ubuntu distros it dosent say which is which.
guess i will have to try a differrent theme or edit a few file within?

okay..now for some advanced options
hope i do the right moves...
F7 at the boot screen or disable folding.

---

### Post by cecilpierce on 2010-01-31
> **bean123 said:**
> Sure, you can edit /boot/burg/themes/winter/theme.txt, add these inside the class section, for example:

```

class {
  ...
  Windows {
    image = "${theme_dir}/os_win.png"
  }

  Ubuntu {
    image = "${theme_dir}/os_ubuntu.png"
  }

  image {
    image = "${theme_dir}/os_unknown.png"
  }
}

```

And copy icons to /boot/burg/themes/winter/.

Thanks, works great, also tried it with ubuntu theme.

---

### Post by richlyn9 on 2010-01-31
> **bean123 said:**
> The option should be --root-directory. Also, /dev/sda means MBR, to install to dedicated partition (hd0,11), use something like this:

```

sudo burg-install --force -–root-directory=/media/Burg /dev/sda11

```

Thanks bean123
that worked in a puff.

i assume i need to run update-burg from /media/Burg  haven't I?

---

### Post by richlyn9 on 2010-01-31
This is what i ran next
something seeems not proper

[COLOR="Indigo"]richlyn@richlyn-personal:~$ sudo burg-install --force --root-directory=/media/Burg /dev/sda11
	/usr/sbin/burg-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/burg-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
Installation finished. No error reported.
richlyn@richlyn-personal:~$ sudo chmod 777 -R /media/Burg
richlyn@richlyn-personal:~$ sudo update-burg
head: cannot open `/boot/burg/video.lst' for reading: No such file or directory
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu lucid (development branch) (10.04) on /dev/sda10
done
richlyn@richlyn-personal:~$ cd /media/Burg
richlyn@richlyn-personal:/media/Burg$ sudo update-burg
head: cannot open `/boot/burg/video.lst' for reading: No such file or directory
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu lucid (development branch) (10.04) on /dev/sda10
done
richlyn@richlyn-personal:/media/Burg$ sudo grub-mkconfig -o /media/Burg/boot/burg/burg.cfg
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu lucid (development branch) (10.04) on /dev/sda10
done
richlyn@richlyn-personal:/media/Burg$ sudo burg-mkconfig -o /media/Burg/boot/burg/burg.cfg
head: cannot open `/boot/burg/video.lst' for reading: No such file or directory
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu lucid (development branch) (10.04) on /dev/sda10
done
richlyn@richlyn-personal:/media/Burg$[/COLOR] 

[B]theres no burg.cfg in the dedicated partition.
how do i correct this?[/B]

---

### Post by bean123 on 2010-01-31
> **richlyn9 said:**
> This is what i ran next
something seeems not proper

[COLOR="Indigo"]richlyn@richlyn-personal:~$ sudo burg-install --force --root-directory=/media/Burg /dev/sda11
	/usr/sbin/burg-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/burg-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
Installation finished. No error reported.
richlyn@richlyn-personal:~$ sudo chmod 777 -R /media/Burg
richlyn@richlyn-personal:~$ sudo update-burg
head: cannot open `/boot/burg/video.lst' for reading: No such file or directory
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu lucid (development branch) (10.04) on /dev/sda10
done
richlyn@richlyn-personal:~$ cd /media/Burg
richlyn@richlyn-personal:/media/Burg$ sudo update-burg
head: cannot open `/boot/burg/video.lst' for reading: No such file or directory
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu lucid (development branch) (10.04) on /dev/sda10
done
richlyn@richlyn-personal:/media/Burg$ sudo grub-mkconfig -o /media/Burg/boot/burg/burg.cfg
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu lucid (development branch) (10.04) on /dev/sda10
done
richlyn@richlyn-personal:/media/Burg$ sudo burg-mkconfig -o /media/Burg/boot/burg/burg.cfg
head: cannot open `/boot/burg/video.lst' for reading: No such file or directory
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu lucid (development branch) (10.04) on /dev/sda10
done
richlyn@richlyn-personal:/media/Burg$[/COLOR] 

[B]theres no burg.cfg in the dedicated partition.
how do i correct this?[/B]

Oh, this is small bug, burg-mkconfig always assume the location of video.lst to be /boot/burg (This affect grub2 too). Anyway, you can just copy video.lst from /media/Burg/boot/burg to /boot/burg. To use graphic menu, you should also copy /boot/burg/fonts and /boot/burg/themes directory to /media/Burg/boot/burg. Then, use this command to generate burg.cfg:

```

sudo burg-mkconfig -o /media/Burg/boot/burg/burg.cfg

```

---

### Post by bean123 on 2010-01-31
> **cecilpierce said:**
> Thanks, works great, also tried it with ubuntu theme.

Oh nice. BTW, a small improvement for this, you can change the template_menuitem section to:

```

template_menuitem {
  panel {
    parameters = "class=image.class:title=text.text"
    direction = left_to_right
    margin_size = 3/0
    space = 1
    image {}
    text {
      valign = center
      font = "Fixed Bold 13"
    }
  }
}

```

space = 1 would insert some space between the icon and text, and valign = center would align the text.

---

### Post by vishalrao on 2010-01-31
LOL @  [http://pavelmachek.livejournal.com/92052.html](http://pavelmachek.livejournal.com/92052.html)

---

### Post by richlyn9 on 2010-01-31
> **bean123 said:**
> Oh, this is small bug, burg-mkconfig always assume the location of video.lst to be /boot/burg (This affect grub2 too). Anyway, you can just copy video.lst from /media/Burg/boot/burg to /boot/burg. To use graphic menu, you should also copy /boot/burg/fonts and /boot/burg/themes directory to /media/Burg/boot/burg. Then, use this command to generate burg.cfg:

```

sudo burg-mkconfig -o /media/Burg/boot/burg/burg.cfg

```

That did fix the bug...
and i have installed burg on a dedicated partition....

Thanks [bean123]("http://ubuntuforums.org/member.php?u=296364") and [starks]("http://ubuntuforums.org/member.php?u=250473") and [vishal]("http://ubuntuforums.org/member.php?u=393222") for starting this great thread

---

### Post by libihero on 2010-01-31
after i installed the burg, the normal ubuntu splash (the white logo on the black background) disappeared
how can i get it back :(

---

### Post by ranch hand on 2010-01-31
> **libihero said:**
> after i installed the burg, the normal ubuntu splash (the white logo on the black background) disappeared
how can i get it back :(
This should not happen.  That splash is plymouth running.

What kind of messages are popping up on your screen that are different now?

---

### Post by Starks on 2010-01-31
> **libihero said:**
> after i installed the burg, the normal ubuntu splash (the white logo on the black background) disappeared
how can i get it back :(
I dunno.

BURG broke Plymouth for me a week or two ago for me as well and purging it didn't help. Just grin and bear it until bean has a solution.

---

### Post by phenest on 2010-01-31
Ok. The font shown in Winter don't work because according to /boot/burg/fonts/font.lst Helvetica Bold 26 doesn't exist. Easy enough. I copied the os icons from refit to winter, copied a bit of code from refit to the class section so the icons show. The icons are quite big so the height needs to be changed to 128. Commented out the background for the menu, and et voila!
```
screen {
  background = "${theme_dir}/dell.png,,light-gray/black"

  panel {
    width = 100%
    height = "14%/3"
  }

  panel {
    id = __menu__
    popup = abs
    extend = 1
    width = 70%
    halign = center
    valign = top

#    top_left = "${theme_dir}/menu_nw.png,,light-gray/black,#0x250F"
#    top = "${theme_dir}/menu_n.png,tiling,light-gray/black,#0x2501"
#    top_right = "${theme_dir}/menu_ne.png,,light-gray/black,#0x2513"
#    left = "${theme_dir}/menu_w.png,tiling,light-gray/black,#0x2503"
#    right = "${theme_dir}/menu_e.png,tiling,light-gray/black,#0x2503"
#    bottom_left = "${theme_dir}/menu_sw.png,,light-gray/black,#0x2517"
#    bottom = "${theme_dir}/menu_s.png,tiling,light-gray/black,#0x2501"
#    bottom_right = "${theme_dir}/menu_se.png,tiling,light-gray/black,#0x251B"
#    background = "${theme_dir}/menu_c.png"
  }

  panel {
    halign = center
    width = 80%
    height = 6%/1
    id = __timeout__
    border_size = 3/0
    border_color = "#000060"

    progressbar {
      width = 100%
      height = 100%
      color = "#C0C0F0/cyan:#6060B0/blue"
    }
  }

  panel {
    margin_size = "10/1"
    text {
      text = "Select an item with the arrow keys and press Enter to boot."
      font = "lime Regular 10"
      color = "#00000/light-gray"
    }
    text {
      text = "Press:  'c' for command line; 'F8' to switch mode."
      font = "lime Regular 10"
      color = "#00000/light-gray"
    }
  }
}

template_submenu {
  panel {
    width = 100%
    height = 100%

    panel {
      id = __child__
      class = frame
      valign = center
      halign = center
      extend = 1
    }
  }
}

template_menuitem {
  panel {
    parameters = "class=image.class:title=text.text"
    height = 128/1
    background = ":${theme_dir}/select_c.png,,black/light-gray,#0"
    direction = left_to_right
    image {}
    text {
      extend = 1
      valign = center
      halign = center
      font = "Helvetica Bold 49"
      color = "#000000/light-gray/black:#CBFBFF/black/light-gray"
    }
  }
}

dialog_line {
  panel {
    parameters = "text=edit.text"
    class = frame
    width = 80%
    attach_hcenter = 0
    attach_vcenter = 0

    edit {
      lines = 1
      max_lines = 1
    }
  }
}

dialog_edit {
  panel {
    parameters = "text=edit.text"
    class = frame
    width = 80%
    attach_hcenter = 0
    attach_vcenter = 0

    edit {
      lines = 10
    }
  }
}

dialog_message {
  panel {
    parameters = "text=text.text"
    class = frame
    margin_size = 1
    margin_bottom = 0
    space = 1
    attach_hcenter = 0
    attach_vcenter = 0
    text {}
    panel {
      class = frame
      command = true
      halign = center
      margin_left = 1
      margin_right = 1
      text { text = OK }
    }
  }
}

dialog_password {
  panel {
    parameters = "username=__user__.text:password=__pass__.text"
    class = frame
    margin_size = 1
    margin_bottom = 0
    attach_hcenter = 0
    attach_vcenter = 0

    panel {
      direction = left_to_right
      space = 1
      text {
        extend = 1
        valign = center
        text = Username
      }
      panel {
        class = frame
        margin_left = 1
        margin_right = 1
        edit {
          id = __user__
          max_lines = 1
        }
      }
    }

    panel {
      direction = left_to_right
      space = 1
      text {
        extend = 1
        valign = center
        text = Password
      }
      panel {
        class = frame
        margin_left = 1
        margin_right = 1
        password {
          id = __pass__
        }
      }
    }

    panel {
      class = frame
      command = true
      halign = center
      margin_left = 1
      margin_right = 1
      text {
        text = OK
      }
    }
  }
}

term_window {
  panel {
    width = 100%
    height = 100%
    top_left = "${theme_dir}/terminal_nw.png,,light-gray/black,#0x250F"
    top = "${theme_dir}/terminal_n.png,tiling,light-gray/black,#0x2501"
    top_right = "${theme_dir}/terminal_ne.png,,light-gray/black,#0x2513"
    left = "${theme_dir}/terminal_w.png,tiling,light-gray/black,#0x2503"
    right = "${theme_dir}/terminal_e.png,tiling,light-gray/black,#0x2503"
    bottom_left = "${theme_dir}/terminal_sw.png,,light-gray/black,#0x2517"
    bottom = "${theme_dir}/terminal_s.png,tiling,light-gray/black,#0x2501"
    bottom_right = "${theme_dir}/terminal_se.png,tiling,light-gray/black,#0x251B"
    background = ",,black,#0"

    term {
      width=100%
      height=100%
    }
  }
}

two_term {
  panel {
    width = 100%
    height = 100%
    direction = left_to_right

    panel {
      class = frame
      extend = 1

      term {
        width=100%
        height=100%
      }
    }

    panel {
      class = frame
      extend = 1

      term {
        width=100%
        height=100%
      }
    }
  }
}

class {
  frame {
    top_left = ",,#000000/cyan/black,#0x250F:,,#000000/light-gray/black,#0x2554"
    top = ",tiling,#000000/cyan/black,#0x2501:,,#000000/light-gray/black,#0x2550"
    top_right = ",,#000000/cyan/black,#0x2513:,,#000000/light-gray/black,#0x2557"
    left = ",tiling,#000000/cyan/black,#0x2503:,,#000000/light-gray/black,#0x2551"
    right = ",tiling,#000000/cyan/black,#0x2503:,,#000000/light-gray/black,#0x2551"
    bottom_left = ",,#000000/cyan/black,#0x2517:,,#000000/light-gray/black,#0x255A"
    bottom = ",tiling,#000000/cyan/black,#0x2501:,,#000000/light-gray/black,#0x2550"
    bottom_right = ",tiling,#000000/cyan/black,#0x251B:,,#000000/light-gray/black,#0x255D"
  }

  text {
    color = "#000000/light-gray/black:black/light-gray"
  }

  term {
    color = "cyan/black:light-gray/black"
  }

  edit {
    color = "#000000/cyan/black:#000000/light-gray/black"
  }

  password {
    color = "#000000/cyan/black:#000000/light-gray/black"
  }

  Windows {
    image = "${theme_dir}/os_win.png"
  }

  Linux {
    image = "${theme_dir}/os_linux.png"
  }

  Ubuntu {
    image = "${theme_dir}/os_ubuntu.png"
  }

  Debian {
    image = "${theme_dir}/os_debian.png"
  }

  SuSE {
    image = "${theme_dir}/os_suse.png"
  }

  FreeBSD {
    image = "${theme_dir}/os_freebsd.png"
  }

  MacOSX {
    image = "${theme_dir}/os_osx.png"
  }

  image {
    image = "${theme_dir}/os_unknown.png"
  }
}
```
I can't give a screenshot, but I've attached the background.

---

### Post by cecilpierce on 2010-01-31
phenest, run sudo burg-emu in a terminal window and then you can take a screenshot, Id like to see the winter theme you made. Im using ubuntu theme because some of my icons blended into the background, thanks

---

### Post by phenest on 2010-01-31
> **cecilpierce said:**
> phenest, run sudo burg-emu in a terminal window and then you can take a screenshot, Id like to see the winter theme you made. Im using ubuntu theme because some of my icons blended into the background, thanks

Of course, why didn't I think of that? It's not winter anymore. It's dell.

The selection bar takes too long to draw, because of the size of the icons. Or I could have an outline instead? Hmmm...

---

### Post by MacUntu on 2010-01-31
Can I somehow remove the "GRUB loading..." part at the very beginning of its start? I looked through sources, but simple grepping wasn't successful. It's the only big font I see during the whole boot process.

Would it also be posible to remove the blinking cursor right before that message?

---

### Post by cecilpierce on 2010-01-31
The dell looks nice, almost like winter, my icons were so big you could only see about a quarter of the top so I used gimp to scale them down.__

---

### Post by cecilpierce on 2010-01-31
forgot to click on upload !

---

### Post by phenest on 2010-01-31
> **cecilpierce said:**
> The dell looks nice, almost like winter, my icons were so big you could only see about a quarter of the top so I used gimp to scale them down.__

I agree the icons are too big, but this was just to see what's possible and how easy. I'll spend more time on this dell theme another time. Right now I'm relaxing with a wee tot of whiskey before I go to bed.

---

### Post by cecilpierce on 2010-01-31
> **phenest said:**
> I agree the icons are too big, but this was just to see what's possible and how easy. I'll spend more time on this dell theme another time. Right now I'm relaxing with a wee tot of whiskey before I go to bed.

I tried debian 1.98~experimental.20100111.1 and all the icons came up the same size no matter what they really were, wish I knew how they did that ?
You must be on the other side of the pond its only 5:00 pm here, enjoy !

---

### Post by phenest on 2010-01-31
I have a question. As someone who uses a dvorak keyboard layout instead of qwerty, using the terminal is tedious. Can I change the layout?

---

### Post by ranch hand on 2010-01-31
I think you can do that in System>Preferences>Keyboard.

---

### Post by phenest on 2010-01-31
> **ranch hand said:**
> I think you can do that in System>Preferences>Keyboard.

How does that affect grub/burg?

---

### Post by ranch hand on 2010-01-31
I thought you were speaking of the keyboard layout.  You can change it for one workstation.  Then it may be easier to change the burg layout in terminal.

---

### Post by richlyn9 on 2010-01-31
i now seeem to have grub2 installed and have also manually got burg...
so instead of downloading the grub2 updates which the update managet does automatically i assume its safe to uninstall grub(grub2)

---

### Post by bean123 on 2010-02-01
> **cecilpierce said:**
> I tried debian 1.98~experimental.20100111.1 and all the icons came up the same size no matter what they really were, wish I knew how they did that ?
You must be on the other side of the pond its only 5:00 pm here, enjoy !

It's quite easy, you just add width and height property to image and it'd scale to the specify size, for example:

```


class {
  ...
  Windows {
    image = "windows.png"
    width = "16/0"
    height = "16/0"
  }
}

```

---

### Post by bean123 on 2010-02-01
> **phenest said:**
> How does that affect grub/burg?

There is a patch on grub-devel list to support keyboard layout. When they merge it to main trunk, I can sync burg to include this feature.

---

### Post by joey-elijah on 2010-02-01
Not been checked in with this thread for a week or so - all change as usual! :p

So i have grub-pc installed but now the package is burg-pc - does one have to uninstall grub-pc, reinstall grub and THEN install burg-pc or can i just installed burg-pc as is?

---

### Post by ranch hand on 2010-02-01
Just install burg.  You can, it seems, run either depending on which you install on the mbr.

---

### Post by ranch hand on 2010-02-01
OK, switched over to the test drive and booted to the burg test OS to  see if I could get some icons on the Ubuntu theme.

I like the theme.  It has nice text and the background is easy to  change.

I changed the bg back to default.  I enabled os-prober.  I ran sudo  update-burg and sudo burg-mkconfig.   I rebooted.

No icons.  I am not big on icons so this does not bother me but it may  be of concern to every one else.  If there are suggestions I will try  them to see  if it will work.

This is a very neat project and I admire the work and effort that has  gone into it but I will not be using it on any production OS.

I can have a custom background in grub with a text menu.  No need to run  os-prober ever with a custom menu.

This is important to me as when you have a bunch of OS' os-prober is not  up to it.  I realize that this is not a burg or grub product but one  used by both.  It sucks.

I hate it when people say something sucks and then drop the subject so  here is my /boot/burg/burg.cfg.  I think that if you look at the  generated entries you will see the reason for my "sucks" opinion;
> 
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
if [ -s $prefix/burgenv ]; then
  load_env
fi
set default="7"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
insmod coreui
menu_region.text
set theme_dir=${prefix}/themes/ubuntu
load_config ${prefix}/themes/conf.d/hotkey
load_config ${theme_dir}/theme.txt
insmod vbe
insmod png
insmod jpeg
set gfxmode=640x480
set gfxfont="Unifont Regular 16"
menu_region.gfx
controller.ext
insmod ext2
set root=(hd0,12)
search --no-floppy --fs-uuid --set d938681d-2c8e-47f7-9d0b-2ff29c760489
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=100
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/09_custom ###
menuentry "Stoner1.2 on sda12" {
    set root=(hd0,12)
        linux /vmlinuz root=/dev/sda12 so quiet splash
        initrd /initrd.img
}
menuentry "Lounge on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 so quiet splash
        initrd /initrd.img
}
menuentry "Lubuntu on sda8" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro quiet splash
        initrd /initrd.img
}
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 so quiet splash
        initrd /initrd.img
}
menuentry "ISO-test on sda14" {
    set root=(hd0,14)
        linux /vmlinuz root=/dev/sda14 ro quiet splash
        initrd /initrd.img
}
menuentry "Mini on sda15" {
    set root=(hd0,15)
        linux /vmlinuz root=/dev/sda15 ro quiet splash
        initrd /initrd.img
}
menuentry "Throw on sda16" {
    set root=(hd0,16)
        linux /vmlinuz root=/dev/sda16 ro quiet splash
        initrd /initrd.img
}
menuentry "StonedLizard on sda17" {
    set root=(hd0,17)
        linux /vmlinuz root=/dev/sda17 ro quiet splash
        initrd /initrd.img
}
menuentry "Zenix on sda11" {
    set root=(hd0,11)
        linux /vmlinuz root=/dev/sda11 so quiet splash
        initrd /initrd.img
}
menuentry "Main, kernel 2.6.24-24-generic (sda6)" {
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-24-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet vga=773
    initrd /boot/initrd.img-2.6.24-24-generic
}
menuentry "Mandriva on sda10" {
    set root=(hd0,10)
        linux /vmlinuz root=/dev/sda10 so quiet splash
        initrd /initrd.img
}
menuentry "Man-Both on sda10" {
        linux (hd0,10)/boot/vmlinuz
        initrd (hd0,10)/boot/initrd.img
}
### END /etc/burg.d/09_custom ###

### BEGIN /etc/burg.d/10_linux ###
menuentry "Ubuntu GNU/Linux, with Linux 2.6.31-17-generic" --class Ubuntu {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set d938681d-2c8e-47f7-9d0b-2ff29c760489
    echo    Loading Linux 2.6.31-17-generic ...
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=d938681d-2c8e-47f7-9d0b-2ff29c760489 ro  quiet
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu GNU/Linux, with Linux 2.6.31-17-generic (recovery mode)" --class Ubuntu {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set d938681d-2c8e-47f7-9d0b-2ff29c760489
    echo    Loading Linux 2.6.31-17-generic ...
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=d938681d-2c8e-47f7-9d0b-2ff29c760489 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-17-generic
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/30_os-prober ###
menuentry "linux (on /dev/sda10)" --class MandrivaLinux {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 17354834-bf70-4bfa-870c-726b83e1b21b
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=17354834-bf70-4bfa-870c-726b83e1b21b resume=UUID=dbc0bfeb-16d9-44f2-8691-3361dfa5ed23 splash=silent vga=788
    initrd (hd0,9)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda10)" --class MandrivaLinux {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 17354834-bf70-4bfa-870c-726b83e1b21b
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=17354834-bf70-4bfa-870c-726b83e1b21b resume=UUID=dbc0bfeb-16d9-44f2-8691-3361dfa5ed23
    initrd (hd0,9)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda10)" --class MandrivaLinux {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 17354834-bf70-4bfa-870c-726b83e1b21b
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=17354834-bf70-4bfa-870c-726b83e1b21b failsafe
    initrd (hd0,9)/boot/initrd.img
}
menuentry "Lounge (on /dev/sda10)" --class MandrivaLinux {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 17354834-bf70-4bfa-870c-726b83e1b21b
    linux boot /vmlinuz root=/dev/sda7 so quiet splash
    initrd /initrd.img
}
menuentry "desktop 2.6.29.1-4mnb (on /dev/sda10)" --class MandrivaLinux {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 17354834-bf70-4bfa-870c-726b83e1b21b
    linux /boot/vmlinuz-2.6.29.1-desktop-4mnb BOOT_IMAGE=desktop_2.6.29.1-4mnb root=UUID=17354834-bf70-4bfa-870c-726b83e1b21b resume=UUID=dbc0bfeb-16d9-44f2-8691-3361dfa5ed23 splash=silent vga=788
    initrd (hd0,9)/boot/initrd-2.6.29.1-desktop-4mnb.img
}
menuentry "desktop 2.6.29.6-2mnb (on /dev/sda10)" --class MandrivaLinux {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 17354834-bf70-4bfa-870c-726b83e1b21b
    linux /boot/vmlinuz-2.6.29.6-desktop-2mnb BOOT_IMAGE=desktop_2.6.29.6-2mnb root=UUID=17354834-bf70-4bfa-870c-726b83e1b21b resume=UUID=dbc0bfeb-16d9-44f2-8691-3361dfa5ed23 splash=silent vga=788
    initrd (hd0,9)/boot/initrd-2.6.29.6-desktop-2mnb.img
}
menuentry "desktop 2.6.29.6-3mnb (on /dev/sda10)" --class MandrivaLinux {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 17354834-bf70-4bfa-870c-726b83e1b21b
    linux /boot/vmlinuz-2.6.29.6-desktop-3mnb BOOT_IMAGE=desktop_2.6.29.6-3mnb root=UUID=17354834-bf70-4bfa-870c-726b83e1b21b resume=UUID=dbc0bfeb-16d9-44f2-8691-3361dfa5ed23 splash=silent vga=788
    initrd (hd0,9)/boot/initrd-2.6.29.6-desktop-3mnb.img
}
menuentry "Zenix on sda11 (on /dev/sda11)" --class Zenix {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 579623c9-0241-41b8-a8ea-30b1dca2d4a4
    linux /vmlinuz root=/dev/sda11 so quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda12 (on /dev/sda11)" --class Zenix {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 579623c9-0241-41b8-a8ea-30b1dca2d4a4
    linux /vmlinuz root=/dev/sda12 so quiet splash
    initrd /initrd.img
}
menuentry "Lounge on sda7 (on /dev/sda11)" --class Zenix {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 579623c9-0241-41b8-a8ea-30b1dca2d4a4
    linux /vmlinuz root=/dev/sda7 so quiet splash
    initrd /initrd.img
}
menuentry "Lubuntu on sda8 (on /dev/sda11)" --class Zenix {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 579623c9-0241-41b8-a8ea-30b1dca2d4a4
    linux /vmlinuz root=/dev/sda8 so quiet splash
    initrd /initrd.img
}
menuentry "Daily on sda13 (on /dev/sda11)" --class Zenix {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 579623c9-0241-41b8-a8ea-30b1dca2d4a4
    linux /vmlinuz root=/dev/sda13 ro quiet splash
    initrd /initrd.img
}
menuentry "ISO-test on sda14 (on /dev/sda11)" --class Zenix {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 579623c9-0241-41b8-a8ea-30b1dca2d4a4
    linux /vmlinuz root=/dev/sda14 ro quiet splash
    initrd /initrd.img
}
menuentry "Mini on sda15 (on /dev/sda11)" --class Zenix {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 579623c9-0241-41b8-a8ea-30b1dca2d4a4
    linux /vmlinuz root=/dev/sda15 ro quiet splash
    initrd /initrd.img
}
menuentry "Throw on sda16 (on /dev/sda11)" --class Zenix {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 579623c9-0241-41b8-a8ea-30b1dca2d4a4
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "Krap on sda17 (on /dev/sda11)" --class Zenix {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 579623c9-0241-41b8-a8ea-30b1dca2d4a4
    linux /vmlinuz root=/dev/sda17 ro quiet splash
    initrd /initrd.img
}
menuentry "Mandriva on sda10 (on /dev/sda11)" --class Zenix {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 579623c9-0241-41b8-a8ea-30b1dca2d4a4
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "Zenix, Linux 2.6.31-17-generic (on /dev/sda11)" --class Zenix {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 579623c9-0241-41b8-a8ea-30b1dca2d4a4
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=579623c9-0241-41b8-a8ea-30b1dca2d4a4 ro quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Zenix, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda11)" --class Zenix {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 579623c9-0241-41b8-a8ea-30b1dca2d4a4
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=579623c9-0241-41b8-a8ea-30b1dca2d4a4 ro single
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Daily on sda13 (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /vmlinuz root=/dev/sda13 ro quiet splash
    initrd /initrd.img
}
menuentry "Lounge on sda7 (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /vmlinuz root=/dev/sda7 ro quiet splash
    initrd /initrd.img
}
menuentry "Lubuntu on sda8 (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /vmlinuz root=/dev/sda8 ro quiet splash
    initrd /initrd.img
}
menuentry "ISO on sda14 (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /vmlinuz root=/dev/sda14 ro quiet splash
    initrd /initrd.img
}
menuentry "Mini on sda15 (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /vmlinuz root=/dev/sda15 ro quiet splash
    initrd /initrd.img
}
menuentry "Throw on sda16 (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "StonedLizard on sda17 (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /vmlinuz root=/dev/sda17 ro quiet splash
    initrd /initrd.img
}
menuentry "Zenix on sda11 (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /vmlinuz root=/dev/sda11 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda12 (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /vmlinuz root=/dev/sda12 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sda6 (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /vmlinuz root=/dev/sda6 ro quiet splash
    initrd /initrd.img
}
menuentry "Mandriva on sda10 (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /boot/vmlinuz-2.6.32-12-generic root=UUID=64ebcaeb-01c4-4c0d-ae2a-fb549789c974 ro quiet splash
    initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode) (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /boot/vmlinuz-2.6.32-12-generic root=UUID=64ebcaeb-01c4-4c0d-ae2a-fb549789c974 ro single
    initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-11-generic (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /boot/vmlinuz-2.6.32-11-generic root=UUID=64ebcaeb-01c4-4c0d-ae2a-fb549789c974 ro quiet splash
    initrd /boot/initrd.img-2.6.32-11-generic
}
menuentry "Ubuntu, with Linux 2.6.32-11-generic (recovery mode) (on /dev/sda13)" --class Ubuntu {
    insmod ext2
    set root=(hd0,13)
    search --no-floppy --fs-uuid --set 64ebcaeb-01c4-4c0d-ae2a-fb549789c974
    linux /boot/vmlinuz-2.6.32-11-generic root=UUID=64ebcaeb-01c4-4c0d-ae2a-fb549789c974 ro single
    initrd /boot/initrd.img-2.6.32-11-generic
}
menuentry "ISO-test on sda14 (on /dev/sda14)" --class Ubuntu1 {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set c87fbeaf-dc3f-4510-826a-c8af1aeca35f
    linux /vmlinuz root=/dev/sda14 ro quiet splash
    initrd /initrd.img
}
menuentry "Lounge on sda7 (on /dev/sda14)" --class Ubuntu1 {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set c87fbeaf-dc3f-4510-826a-c8af1aeca35f
    linux /vmlinuz root=/dev/sda7 ro quiet splash
    initrd /initrd.img
}
menuentry "Lubuntu on sda8 (on /dev/sda14)" --class Ubuntu1 {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set c87fbeaf-dc3f-4510-826a-c8af1aeca35f
    linux /vmlinuz root=/dev/sda8 ro quiet splash
    initrd /initrd.img
}
menuentry "Daily on sda13 (on /dev/sda14)" --class Ubuntu1 {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set c87fbeaf-dc3f-4510-826a-c8af1aeca35f
    linux /vmlinuz root=/dev/sda13 ro quiet splash
    initrd /initrd.img
}
menuentry "Mini on sda15 (on /dev/sda14)" --class Ubuntu1 {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set c87fbeaf-dc3f-4510-826a-c8af1aeca35f
    linux /vmlinuz root=/dev/sda15 ro quiet splash
    initrd /initrd.img
}
menuentry "Throw on sda16 (on /dev/sda14)" --class Ubuntu1 {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set c87fbeaf-dc3f-4510-826a-c8af1aeca35f
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "StonedLizard on sda17 (on /dev/sda14)" --class Ubuntu1 {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set c87fbeaf-dc3f-4510-826a-c8af1aeca35f
    linux /vmlinuz root=/dev/sda17 ro quiet splash
    initrd /initrd.img
}
menuentry "HornyHorse on sdg6 (on /dev/sda14)" --class Ubuntu1 {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set c87fbeaf-dc3f-4510-826a-c8af1aeca35f
    linux /vmlinuz root=/dev/sdg6 ro quiet splash
    initrd /initrd.img
}
menuentry "HornyHorse on sdg6 Recovery (on /dev/sda14)" --class Ubuntu1 {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set c87fbeaf-dc3f-4510-826a-c8af1aeca35f
    linux /vmlinuz root=/dev/sdg6 ro single
    initrd /initrd.img
}
menuentry "Zenix on sda11 (on /dev/sda14)" --class Ubuntu1 {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set c87fbeaf-dc3f-4510-826a-c8af1aeca35f
    linux /vmlinuz root=/dev/sda11 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda12 (on /dev/sda14)" --class Ubuntu1 {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set c87fbeaf-dc3f-4510-826a-c8af1aeca35f
    linux /vmlinuz root=/dev/sda12 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sda6 (on /dev/sda14)" --class Ubuntu1 {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set c87fbeaf-dc3f-4510-826a-c8af1aeca35f
    linux /vmlinuz root=/dev/sda6 ro quiet splash
    initrd /initrd.img
}
menuentry "Mandriva on sda10 (on /dev/sda14)" --class Ubuntu1 {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set c87fbeaf-dc3f-4510-826a-c8af1aeca35f
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "Mini on sda15 (on /dev/sda15)" --class Ubuntu2 {
    insmod ext2
    set root=(hd0,15)
    search --no-floppy --fs-uuid --set 8bcf3de7-be3f-47ab-a658-8c2467658947
    linux /vmlinuz root=/dev/sda15 ro quiet splash
    initrd /initrd.img
}
menuentry "Lounge on sda7 (on /dev/sda15)" --class Ubuntu2 {
    insmod ext2
    set root=(hd0,15)
    search --no-floppy --fs-uuid --set 8bcf3de7-be3f-47ab-a658-8c2467658947
    linux /vmlinuz root=/dev/sda7 ro quiet splash
    initrd /initrd.img
}
menuentry "Lubuntu on sda8 (on /dev/sda15)" --class Ubuntu2 {
    insmod ext2
    set root=(hd0,15)
    search --no-floppy --fs-uuid --set 8bcf3de7-be3f-47ab-a658-8c2467658947
    linux /vmlinuz root=/dev/sda8 ro quiet splash
    initrd /initrd.img
}
menuentry "Daily on sda13 (on /dev/sda15)" --class Ubuntu2 {
    insmod ext2
    set root=(hd0,15)
    search --no-floppy --fs-uuid --set 8bcf3de7-be3f-47ab-a658-8c2467658947
    linux /vmlinuz root=/dev/sda13 ro quiet splash
    initrd /initrd.img
}
menuentry "ISO-test on sda14 (on /dev/sda15)" --class Ubuntu2 {
    insmod ext2
    set root=(hd0,15)
    search --no-floppy --fs-uuid --set 8bcf3de7-be3f-47ab-a658-8c2467658947
    linux /vmlinuz root=/dev/sda14 ro quiet splash
    initrd /initrd.img
}
menuentry "Throw on sda16 (on /dev/sda15)" --class Ubuntu2 {
    insmod ext2
    set root=(hd0,15)
    search --no-floppy --fs-uuid --set 8bcf3de7-be3f-47ab-a658-8c2467658947
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "StonedLizard on sda17 (on /dev/sda15)" --class Ubuntu2 {
    insmod ext2
    set root=(hd0,15)
    search --no-floppy --fs-uuid --set 8bcf3de7-be3f-47ab-a658-8c2467658947
    linux /vmlinuz root=/dev/sda17 ro quiet splash
    initrd /initrd.img
}
menuentry "Zenix on sda11 (on /dev/sda15)" --class Ubuntu2 {
    insmod ext2
    set root=(hd0,15)
    search --no-floppy --fs-uuid --set 8bcf3de7-be3f-47ab-a658-8c2467658947
    linux /vmlinuz root=/dev/sda11 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda12 (on /dev/sda15)" --class Ubuntu2 {
    insmod ext2
    set root=(hd0,15)
    search --no-floppy --fs-uuid --set 8bcf3de7-be3f-47ab-a658-8c2467658947
    linux /vmlinuz root=/dev/sda12 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sda6 (on /dev/sda15)" --class Ubuntu2 {
    insmod ext2
    set root=(hd0,15)
    search --no-floppy --fs-uuid --set 8bcf3de7-be3f-47ab-a658-8c2467658947
    linux /vmlinuz root=/dev/sda6 ro quiet splash
    initrd /initrd.img
}
menuentry "Mandriva on sda10 (on /dev/sda15)" --class Ubuntu2 {
    insmod ext2
    set root=(hd0,15)
    search --no-floppy --fs-uuid --set 8bcf3de7-be3f-47ab-a658-8c2467658947
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "Throw on sdb16 (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /vmlinuz root=/dev/sdb16 ro quiet splash
    initrd /initrd.img
}
menuentry "StonedLizard on sda17 (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /vmlinuz root=/dev/sda17 ro quiet splash
    initrd /initrd.img
}
menuentry "Lounge on sdb7 (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /vmlinuz root=/dev/sdb7 ro quiet splash
    initrd /initrd.img
}
menuentry "Lubuntu on sdb8 (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /vmlinuz root=/dev/sdb8 ro quiet splash
    initrd /initrd.img
}
menuentry "Daily on sdb13 (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /vmlinuz root=/dev/sdb13 ro quiet splash
    initrd /initrd.img
}
menuentry "ISO-test on sdb14 (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /vmlinuz root=/dev/sdb14 ro quiet splash
    initrd /initrd.img
}
menuentry "Mini on sdb15 (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /vmlinuz root=/dev/sdb15 ro quiet splash
    initrd /initrd.img
}
menuentry "StonedLizard on sdb17 (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /vmlinuz root=/dev/sdb17 ro quiet splash
    initrd /initrd.img
}
menuentry "Zenix on sdb11 (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /vmlinuz root=/dev/sdb11 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sdb12 (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /vmlinuz root=/dev/sdb12 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sdb6 (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /vmlinuz root=/dev/sdb6 ro quiet splash
    initrd /initrd.img
}
menuentry "KinkyFR on sda9 (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /vmlinuz root=/dev/sda9 so quiet splash
    initrd /initrd.img
}
menuentry "PhatDebian on sda7 (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /vmlinuz root=/dev/sda7 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /boot/vmlinuz-2.6.32-12-generic root=UUID=f09ea675-daed-4fbf-885f-23041465735a ro quiet splash
    initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode) (on /dev/sda16)" --class Ubuntu3 {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set f09ea675-daed-4fbf-885f-23041465735a
    linux /boot/vmlinuz-2.6.32-12-generic root=UUID=f09ea675-daed-4fbf-885f-23041465735a ro single
    initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "StonedLizard on sda17 (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda17 ro quiet splash
    initrd /initrd.img
}
menuentry "Lounge on sda7 (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda7 ro quiet splash
    initrd /initrd.img
}
menuentry "Lubuntu on sda8 (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda8 ro quiet splash
    initrd /initrd.img
}
menuentry "Daily on sda13 (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda13 ro quiet splash
    initrd /initrd.img
}
menuentry "ISO-test on sda14 (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda14 ro quiet splash
    initrd /initrd.img
}
menuentry "Mini on sda15 (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda15 ro quiet splash
    initrd /initrd.img
}
menuentry "Throw on sda16 (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "Zenix on sda11 (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda11 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda12 (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda12 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sda6 (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda6 ro quiet splash
    initrd /initrd.img
}
menuentry "Mandriva on sda10 (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /boot/vmlinuz-2.6.32-12-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro quiet splash
    initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode) (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /boot/vmlinuz-2.6.32-12-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro single
    initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-11-generic (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /boot/vmlinuz-2.6.32-11-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro quiet splash
    initrd /boot/initrd.img-2.6.32-11-generic
}
menuentry "Ubuntu, with Linux 2.6.32-11-generic (recovery mode) (on /dev/sda17)" --class Ubuntu4 {
    insmod ext2
    set root=(hd0,17)
    search --no-floppy --fs-uuid --set 9e1065f7-6ec2-4dde-9f15-13a5b304e318
    linux /boot/vmlinuz-2.6.32-11-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro single
    initrd /boot/initrd.img-2.6.32-11-generic
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (on /dev/sda6)" --class Ubuntu5 {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-26-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet vga=773
    initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sda6)" --class Ubuntu5 {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-26-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
    initrd /boot/initrd.img-2.6.24-26-generic
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (on /dev/sda6)" --class Ubuntu5 {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-24-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet vga=773
    initrd /boot/initrd.img-2.6.24-24-generic
}
menuentry "Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode) (on /dev/sda6)" --class Ubuntu5 {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/vmlinuz-2.6.24-24-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro single
    initrd /boot/initrd.img-2.6.24-24-generic
}
menuentry "Ubuntu 8.04.3 LTS, memtest86+ (on /dev/sda6)" --class Ubuntu5 {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
    linux /boot/memtest86+.bin 
}
menuentry "Lounge on sda7 (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda7 ro quiet splash
    initrd /initrd.img
}
menuentry "Lubuntu on sda8 (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda8 ro quiet splash
    initrd /initrd.img
}
menuentry "Daily on sda13 (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda13 ro quiet splash
    initrd /initrd.img
}
menuentry "ISO-test on sda14 (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda14 ro quiet splash
    initrd /initrd.img
}
menuentry "Mini on sda15 (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda15 ro quiet splash
    initrd /initrd.img
}
menuentry "Throw on sda16 (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda16 ro quiet splash
    initrd /initrd.img
}
menuentry "StonedLizard on sda17 (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda17 ro quiet splash
    initrd /initrd.img
}
menuentry "HornyHorse on sdg6 (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sdg6 ro quiet splash
    initrd /initrd.img
}
menuentry "HornyHorse on sdg6 Recovery (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sdg6 ro single
    initrd /initrd.img
}
menuentry "Zenix on sda11 (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda11 ro quiet splash
    initrd /initrd.img
}
menuentry "Stoner1.2 on sda12 (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda12 ro quiet splash
    initrd /initrd.img
}
menuentry "Main on sda6 (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda6 ro quiet splash
    initrd /initrd.img
}
menuentry "Mandriva on sda10 (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /vmlinuz root=/dev/sda10 so quiet splash
    initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.32-12-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro quiet splash
    initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode) (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.32-12-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro single
    initrd /boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-11-generic (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.32-11-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro quiet splash
    initrd /boot/initrd.img-2.6.32-11-generic
}
menuentry "Ubuntu, with Linux 2.6.32-11-generic (recovery mode) (on /dev/sda7)" --class Ubuntu6 {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2c8a03b5-c05f-4663-8c14-e75db877288a
    linux /boot/vmlinuz-2.6.32-11-generic root=UUID=2c8a03b5-c05f-4663-8c14-e75db877288a ro single
    initrd /boot/initrd.img-2.6.32-11-generic
}

### END /etc/burg.d/30_os-prober ###

Kind of big and useless as can be seen in the vast number of incorrect generated entries.  I had to edit out the entire sda8 sequence of entries because the 8 generates a smiley.  Way too many for the post to go through.

I will be happy to do things to this burg installation if anyone has something they would like me to try.  But no I will not be using it as a replacement for grub at this time anywhere else.

---

### Post by bean123 on 2010-02-01
New version burg 1.98+20100201-1 and burg-themes 1.98+20100201-1

* Add theme selection menu.
Use hotkey 't' to open the theme selection menu. You can change theme dynamically. The default value of GRUB_THEME is:

GRUB_THEME=saved

which means use the last selected theme.

* Change folding option dynamically
Use hotkey 'f' to toggle between folding modes. The default value of GRUB_FOLD is:

GRUB_FOLD=saved

which means use the last folding option.

With these settings, you don't need to edit /etc/default/burg anymore. Theme and folding can be changed at runtime.

* New hotkey 'n', 'w' and 'u'
'n' jumps to the the next boot item with the same class
'w' jumps to the next Windows item
'u' jumps to the next Ubuntu item

* grub-emu now uses host as default device.
You can skip "-r host" now

* Support theme template
Custom theme is very easy now. For example, to customize ubuntu theme, create a directory such as /boot/burg/themes/my_theme, then create a theme file inside it:

```

include "../ubuntu/theme"

```

Run update-burg, now the 't' hotkey in boot menu would show the new theme my_theme. Its function is identical to ubuntu.

To change the background image, copy it to /boot/burg/themes/my_theme, and modify theme as:
```

include "../ubuntu/theme"

+screen {
  background="$$/background.png"
}

```

The + prefix mean merge this setting into the screen section. $$ expands into the current directory.

To add icons for unknown class, copy image to /boot/burg/themes/my_theme, and modify theme as:
```

include "../ubuntu/theme"

+screen {
  background="$$/background.png"
}

+class {
  -OS1 {
    image="$$/os1.png"
  }
  -OS2 {
    image="$$/os2.png"
  }
}

```

The - prefix mean replace, you can use this to overwrite icon already defined in ubuntu. The default icon is at /boot/burg/themes/icons. Ubuntu uses small icon which is 24x24. refit uses large icon 128x128.

---

### Post by richlyn9 on 2010-02-01
> **ranch hand said:**
> Just install burg.  You can, it seems, run either depending on which you install on the mbr.

So i guess that i need not uninstall grub and any futher grub updates by update manager will not harm the mbr.

---

### Post by bean123 on 2010-02-01
> **richlyn9 said:**
> So i guess that i need not uninstall grub and any futher grub updates by update manager will not harm the mbr.

Yeah, I have changed the program prefix so that it won't conflict with grub, you can installed both.

---

### Post by phenest on 2010-02-01
> **bean123 said:**
> There is a patch on grub-devel list to support keyboard layout. When they merge it to main trunk, I can sync burg to include this feature.

Excellent! Trying to remember qwerty is a pain.

---

### Post by phenest on 2010-02-01
> **bean123 said:**
> New version burg 1.98+20100201-1 and burg-themes 1.98+20100201-1

* Add theme selection menu.
Use hotkey 't' to open the theme selection menu. You can change theme dynamically. The default value of GRUB_THEME is:

GRUB_THEME=saved

which means use the last selected theme.

* Change folding option dynamically
Use hotkey 'f' to toggle between folding modes. The default value of GRUB_FOLD is:

GRUB_FOLD=saved

which means use the last folding option.

With these settings, you don't need to edit /etc/default/burg anymore. Theme and folding can be changed at runtime.

Really nice and works perfectly, but not in burg-emu.

---

### Post by cecilpierce on 2010-02-01
yep! Sure would be nice to have that emu working, I have to reboot to see what all I messed up.
I spent half today getting the old burg the way I liked it, now I have a new one to figure out, FUN

Thanks bean123, its getting better.

---

### Post by elitenoobboy on 2010-02-01
Grub2 seems to not want to listen to what I tell it to do in my configuration. I want it to go to 1920x1200 resolution, but for some reason, it only seems to load at around 1280x1024 res. The /boot/grub/grub.cfg file is as follows:
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1920x1200
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
set locale_dir=/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
insmod png
if background_image /usr/share/images/grub/7.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-12-generic" {
        recordfail
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
	linux	/boot/vmlinuz-2.6.32-12-generic root=UUID=e0f26c9c-07bd-4cc3-b475-fa77777af0d9 ro splash vga=795  splash
	initrd	/boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-12-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
	echo	Loading Linux 2.6.32-12-generic ...
	linux	/boot/vmlinuz-2.6.32-12-generic root=UUID=e0f26c9c-07bd-4cc3-b475-fa77777af0d9 ro single splash vga=795
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic" {
        recordfail
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=e0f26c9c-07bd-4cc3-b475-fa77777af0d9 ro splash vga=795  splash
	initrd	/boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
	echo	Loading Linux 2.6.32-10-generic ...
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=e0f26c9c-07bd-4cc3-b475-fa77777af0d9 ro single splash vga=795
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-9-generic" {
        recordfail
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
	linux	/boot/vmlinuz-2.6.32-9-generic root=UUID=e0f26c9c-07bd-4cc3-b475-fa77777af0d9 ro splash vga=795  splash
	initrd	/boot/initrd.img-2.6.32-9-generic
}
menuentry "Ubuntu, with Linux 2.6.32-9-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
	echo	Loading Linux 2.6.32-9-generic ...
	linux	/boot/vmlinuz-2.6.32-9-generic root=UUID=e0f26c9c-07bd-4cc3-b475-fa77777af0d9 ro single splash vga=795
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-9-generic
}
menuentry "Ubuntu, with Linux 2.6.32-7-generic" {
        recordfail
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
	linux	/boot/vmlinuz-2.6.32-7-generic root=UUID=e0f26c9c-07bd-4cc3-b475-fa77777af0d9 ro splash vga=795  splash
	initrd	/boot/initrd.img-2.6.32-7-generic
}
menuentry "Ubuntu, with Linux 2.6.32-7-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
	echo	Loading Linux 2.6.32-7-generic ...
	linux	/boot/vmlinuz-2.6.32-7-generic root=UUID=e0f26c9c-07bd-4cc3-b475-fa77777af0d9 ro single splash vga=795
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-7-generic
}
menuentry "Ubuntu, with Linux 2.6.32-6-generic" {
        recordfail
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
	linux	/boot/vmlinuz-2.6.32-6-generic root=UUID=e0f26c9c-07bd-4cc3-b475-fa77777af0d9 ro splash vga=795  splash
	initrd	/boot/initrd.img-2.6.32-6-generic
}
menuentry "Ubuntu, with Linux 2.6.32-6-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
	echo	Loading Linux 2.6.32-6-generic ...
	linux	/boot/vmlinuz-2.6.32-6-generic root=UUID=e0f26c9c-07bd-4cc3-b475-fa77777af0d9 ro single splash vga=795
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-6-generic
}
menuentry "Ubuntu, with Linux 2.6.31-15-generic" {
        recordfail
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=e0f26c9c-07bd-4cc3-b475-fa77777af0d9 ro splash vga=795  splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, with Linux 2.6.31-15-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set e0f26c9c-07bd-4cc3-b475-fa77777af0d9
	echo	Loading Linux 2.6.31-15-generic ...
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=e0f26c9c-07bd-4cc3-b475-fa77777af0d9 ro single splash vga=795
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.31-15-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 1ef45c08f45be097
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```
Can anybody tell me what I need to do to get it to work right? I am a bit new to modifying the files in /etc/grub.d/ and am not sure why it is not listening to me. Back when I had 1.97beta it would load the correct res, but after I upgraded to 1.98~20100115, I told it to wipe the old config files because it had changed since then, and now I can't seem to get it back.

Also, for some reason, I am not getting a splash image with text when it loads ubuntu. I only get a splash without text even though I have made sure that it does not boot with "quiet".

---

### Post by bean123 on 2010-02-02
> **cecilpierce said:**
> yep! Sure would be nice to have that emu working, I have to reboot to see what all I messed up.
I spent half today getting the old burg the way I liked it, now I have a new one to figure out, FUN

Thanks bean123, its getting better.

It works in burg-emu too, use this command:

```

sudo burg-emu -D

```

The -D option allows burg-emu to access physical disk, so that it can load/save environment. It used to be the default, but I'm afraid accessing disk may have some risk so I use host fs as default now.

---

### Post by gspat on 2010-02-02
I have a silly request for you bean...

burg is gorgeous! My daughter saw the results of what I had played with and was VERY impressed.

Would it be possible to have burg do a check at startup to see what res you are able to use and pick an image based on it?

ie:

800x600.png
1024x768.png
1900x1200.png

It's really easy for me to resize an image that I want to use, but if I use an image too large, burg will chop the right side and the bottom off (to the screen size) and displace the icons if I specify an incorrect size.

If it could figure what the best rez was automatically, and use the proper size image accordingly, it would make theme creation amazingly simple for a large variety of machines at once (one theme, good for best rez of any machine you pass it on to).

thanks for reading!

---

### Post by cecilpierce on 2010-02-02
bean123

* Support theme template
Custom theme is very easy now. For example, to customize ubuntu theme, create a directory such as /boot/burg/themes/my_theme, then create a theme file inside it:

Code:

include "../ubuntu/theme"

I tried this and must have done something wrong or I don't understand what to do, it don't come up in the 't' menu. Sorry to be a pain in the neck ! haha

Sorry, my mistake.

---

### Post by McDuff on 2010-02-02
> **cecilpierce said:**
> 
I tried this and must have done something wrong or I don't understand what to do, it don't come up in the 't' menu. Sorry to be a pain in the neck ! haha

I had this problem too—lack of reading carefully.

You have to do ```
sudo update-burg
``` so burg knows about my_theme.

---

### Post by cecilpierce on 2010-02-02
WOW, am I dumb, I just though about that and didn't remember to do update-burg, just tried it in emu -D and it came up making me feel like a dodo bird !!!
Thanks for the help, next time I'll wait till my brain calms down a bit.

---

### Post by bean123 on 2010-02-02
New package burg 1.98+20100202-1 and burg-themes burg 1.98+20100202-1

* Support circular progress bar, the new theme ubuntu2 illustrate this feature.

* Special handling for host device in burg-emu
You don't need to access disk to save/load variable, this works now:
```

sudo burg-emu

```

* Add lots of OS icons, which includes:
Windows, Linux, Ubuntu, Debian, SuSE, FreeBSD, OSX, Gentoo, Mint, Mandrake/Mandriva, Arch, CentOS, Fedora, Mepis, PCLinuxOS, Puppy, RedHat, Sabayon, Slackware, Zenix.

Although os-prober may not detect class label properly for some of them.

---

### Post by bean123 on 2010-02-02
> **gspat said:**
> I have a silly request for you bean...

burg is gorgeous! My daughter saw the results of what I had played with and was VERY impressed.

Would it be possible to have burg do a check at startup to see what res you are able to use and pick an image based on it?

ie:

800x600.png
1024x768.png
1900x1200.png

It's really easy for me to resize an image that I want to use, but if I use an image too large, burg will chop the right side and the bottom off (to the screen size) and displace the icons if I specify an incorrect size.

If it could figure what the best rez was automatically, and use the proper size image accordingly, it would make theme creation amazingly simple for a large variety of machines at once (one theme, good for best rez of any machine you pass it on to).

thanks for reading!

Yeah, I have thought of similar issue. Perhaps we can support multiple class sections, like class.800x600, class.1024x768, class.text, etc. Then we can have different setting in different modes.

---

### Post by krash1220 on 2010-02-05
> **cecilpierce said:**
> Thanks, works great, also tried it with ubuntu theme.

class {
  ...
  Windows {
    image = "${theme_dir}/os_win.png"
  }

  Ubuntu {
    image = "${theme_dir}/os_ubuntu.png"
  }

  image {
    image = "${theme_dir}/os_unknown.png"
  }
}


Okay, that's what I tried to do in the ubuntu theme but when I insert that under the class section, I end up with not icons at all. 

Can you paste what your theme file looks like for me?

---

### Post by bean123 on 2010-02-05
> **krash1220 said:**
> class {
  ...
  Windows {
    image = "${theme_dir}/os_win.png"
  }

  Ubuntu {
    image = "${theme_dir}/os_ubuntu.png"
  }

  image {
    image = "${theme_dir}/os_unknown.png"
  }
}


Okay, that's what I tried to do in the ubuntu theme but when I insert that under the class section, I end up with not icons at all. 

Can you paste what your theme file looks like for me?

The latest burg-themes package already includes icons for many OS. If you want to add more, you should use the new syntax $$, for example:

```

  MY_OS {
    image = "$$/my_os.png"
  }

```

Make sure to replace MY_OS with the proper class label.

---

### Post by krash1220 on 2010-02-05
> **bean123 said:**
> The latest burg-themes package already includes icons for many OS. If you want to add more, you should use the new syntax $$, for example:

```

  MY_OS {
    image = "$$/my_os.png"
  }

```Make sure to replace MY_OS with the proper class label.


Never mind, I figured it out. I had to edit the small file in the icons folder. I just wanted to say, I absolutely love the themes. Thank you for all your hard work.

---

### Post by krash1220 on 2010-02-05
What I can't figure out now, is how to change the menu font. I would like the ubuntu theme menu font to be bold and bigger but no matter what I try, it doesn't change.

---

### Post by cecilpierce on 2010-02-05
Yea me to, I also put the circle timer in the winter theme but could not get rid of the old timer bar at the bottom.

Wish there was a dictionary on this !

---

### Post by phenest on 2010-02-05
> **cecilpierce said:**
> Wish there was a dictionary on this !

There is. Look at my signature.

---

### Post by krash1220 on 2010-02-05
Well, I think it needs to be updated because the commands grub-pc are no longer correct.And I read the whole thing and I still don't know how to change the font size.

---

### Post by cecilpierce on 2010-02-05
Re: GRUB2 theming for lucid?
Quote:
Originally Posted by cecilpierce View Post
Wish there was a dictionary on this !
There is. Look at my signature.
__________________
"Knowledge is power. Who said that?" - Dave Lister
The biggest problem with computers is the bit between the keyboard and the chair.
Gnome Shell & Azenis - Burg 

Thanks, it will take awhile to soak all that in !

---

### Post by krash1220 on 2010-02-05
> **bean123 said:**
> First you need to open /boot/burg/fonts/font.lst to see what fonts are available, then you can replace the font parameter, for example "Fixed Regular 20".

You can use burg-mkfont to generate new fonts, -h option to show all options, for example:

```

burg-mkfont -o my_font.pf2 -s 20 my_font.bdf

```You can also convert TTF.

Then, copy my_font.pf2 to /boot/burg/fonts, and use the following command to update the font list:

```

cd /boot/burg/fonts
sudo burg-mkfont -i *.pf2 > font.lst

```


aaaahhhh, I finally got it. I wasn't changing the font to a font that was available in the in the font.lst.

---

### Post by phenest on 2010-02-05
Every time an upgrade requires grub to be updated, I have to run sudo burg-install "(hd0)" to get back to burg. Is there a way to get the grub update to run burg instead?

---

### Post by ranch hand on 2010-02-05
Do not have grub installed on the mbr.  You get the option.  Leave it blank or install on the partition (not a real good idea but I am not sure you can leave it blank).

---

### Post by cecilpierce on 2010-02-05
> **phenest said:**
> Every time an upgrade requires grub to be updated, I have to run sudo burg-install "(hd0)" to get back to burg. Is there a way to get the grub update to run burg instead?

I think you can 'lock version' under package in synapic and it won't upgrade grub any more, just an idea.

---

### Post by phenest on 2010-02-05
> **cecilpierce said:**
> I think you can 'lock version' under package in synapic and it won't upgrade grub any more, just an idea.

That's not what I meant. If there is an upgraded kernel, for example, grub gets configured again which in turn over writes the mbr so I have to re-install burg to the mbr.

---

### Post by cecilpierce on 2010-02-05
> **phenest said:**
> That's not what I meant. If there is an upgraded kernel, for example, grub gets configured again which in turn over writes the mbr so I have to re-install burg to the mbr.

OK, dont have a clue, mab=ybe remove grub or bean123 has the answer, sorry

---

### Post by BwackNinja on 2010-02-05
> **phenest said:**
> That's not what I meant. If there is an upgraded kernel, for example, grub gets configured again which in turn over writes the mbr so I have to re-install burg to the mbr.

sudo mv /usr/sbin/update-grub /usr/sbin/update-grub.bak
sudo ln -s /usr/sbin/update-burg /usr/sbin/update-grub

---

### Post by phenest on 2010-02-05
> **BwackNinja said:**
> sudo mv /usr/sbin/update-grub /usr/sbin/update-grub.bak
sudo ln -s /usr/sbin/update-burg /usr/sbin/update-grub

Thanks for that.

---

### Post by ranch hand on 2010-02-05
> **ranch hand said:**
> Do not have grub installed on the mbr.  You get the option.  Leave it blank or install on the partition (not a real good idea but I am not sure you can leave it blank).
Seeing how we had updates today for grub1.98 I gave it a whack.  You can leave it blank.

You do get a warning and must tab/enter to change the default "no" to "yes" when you are asked something like "do you really want to do this dumb move".  See how I upgrade this OS last - yes I really do.

---

### Post by vishalrao on 2010-02-06
To run BURG's burg-install instead of GRUB's grub-install everytime there is an update to GRUB, would simply adding an alias in bash profile (of the user and/or root) work instead of messing with dpkg/config/symlinks?

---

### Post by phenest on 2010-02-06
> **ranch hand said:**
> Seeing how we had updates today for grub1.98 I gave it a whack.  You can leave it blank.

Leave what blank?

---

### Post by ranch hand on 2010-02-06
Where you install grub on the mbr when upgrading it.  I like the option but do wonder how many folks are going to screw their ability to boot.

---

### Post by richlyn9 on 2010-02-07
I have messed things up now(happy that i will learn something new though!!!).

[B]I have a triple boot with karmic,windows xp and lucid testing
I have installed Burg on a dedicated partitio[/B]n

I was running a partial upgrade when burg-pc got updated(it gave me an option but since i had multiple windows opened i missed and it installed the new version by mistake)Whatever it did MBR wont detect any linux installs(???)
MBR's back to the traditional black screen with just windows XP option.

Firstly i dont know why did a lucid update/upgrade mess things(aren't dedicated partition burg install meant to avoid such situations or maybe i had not installed the burg to the dedicated correctly. Whatever but i would like to get this fixed ASAP

So what do i do with a live CD?

---

### Post by richlyn9 on 2010-02-07
i booted with a live  CD and mounted the Burg partition
and tried these 

custom@custom:~$ sudo burg-mkconfig -o /media/Burg/boot/burg/burg.cfg
sudo: burg-mkconfig: command not found
custom@custom:~$ sudo burg-install --force --root-directory=/media/Burg /dev/sda11
sudo: burg-install: command not found
custom@custom:~$ 

custom@custom:~$ sudo burg-install sda11
sudo: burg-install: command not found
custom@custom:~$ burg-install sda11
bash: burg-install: command not found
custom@custom:/media/Burg/boot/burg$ sudo burg-mkconfig -o /media/Burg/boot/burg/burg.cfg
sudo: burg-mkconfig: command not found
custom@custom:/media/Burg/boot/burg$ sudo burg-install --force --root-directory=/media/Burg /dev/sda11
sudo: burg-install: command not found
custom@custom:/media/Burg/boot/burg$ 

nothing works
kindly help

---

### Post by ranch hand on 2010-02-07
Try;
```

sudo burg-install "(hd0,11)"

```
I believe that will do it.

Your upgrade was for grub-pc and grub-common and that ran the install command and put it on your mbr.

---

### Post by purplefuku on 2010-02-07
I'm having a very similar problem to richlyn9. Dual boot with XP. Ran the burg update. It detected my partitons fine, but will only show me Windows XP on the menu. I booted into the LiveCD and tried to restore, but it's giving me "command not found" errors every time...

Everything was working fine before the update...

---

### Post by richlyn9 on 2010-02-08
> **purplefuku said:**
> I booted into the LiveCD and tried to restore, but it's giving me "command not found" errors every time...


same here!!!

custom@custom:~$ sudo burg-install "(hd0,11)"
sudo: burg-install: command not found
custom@custom:~$ sudo burg-install (hd0,11)
bash: syntax error near unexpected token `('
custom@custom:~$ sudo burg-install sda11
sudo: burg-install: command not found
custom@custom:~$

---

### Post by ranch hand on 2010-02-08
I can believe that.  Burg is not on the LiveCD.

You can't run things like "grub-install /dev/sda" from a 9.04 LiveCD either.

If you still have (I assume you do) grub on install it and get booted and then do the Burg stuff from the OS unless you have another install that has Burg that you can chroot in from.

---

### Post by richlyn9 on 2010-02-08
i think that the live cd that i boot in with is 8.10 an old version and that the repos for burg  are not listed in the sources list that may be  a reason why i get that error.

can i somehow get and run a terminal from karmic or lucid within the live CD?

---

### Post by richlyn9 on 2010-02-08
> **ranch hand said:**
> I can believe that.  Burg is not on the LiveCD.

You can't run things like "grub-install /dev/sda" from a 9.04 LiveCD either.

If you still have (I assume you do) grub on install it and get booted and then do the Burg stuff from the OS **unless you have another install that has Burg that you can chroot in from**.

thought as much!!
 ranch hand :what do you mean by"**unless you have another install that has Burg that you can chroot in from**"
 i have burg installed in lucid and karmic can i install burg from there somehow? if possible how?
i dont know whats chroot :(

---

### Post by ranch hand on 2010-02-08
> **richlyn9 said:**
> thought as much!!
 ranch hand :what do you mean by"**unless you have another install that has Burg that you can chroot in from**"
 i have burg installed in lucid and karmic can i install burg from there somehow? if possible how?
i dont know whats chroot :(
I didn't know a thing about chroot until the 9.10-testing cycle.  Take my work for it, this OS is trouble free and boring.

I have 7 10.04 installs on an external enclosure with 2 320Gb drives (and some other OS' to play with).  I have one that I use as my "production" OS in the daytime (I am on a 9.04 respin right now on my main internal drive).

When I boot up in the morning I run updates from that OS (Stoned Liazrd) on the other 6.  Two of those six get upgraded at that time.  I boot to them to see if they work before upgrading any others.

Phillinux posted this script back in the 9.10-testing forum;
```

#!/bin/sh

sudo mkdir /mnt/Jaunty-64-root
sudo mount /dev/sda3 /mnt/Jaunty-64-root/
sudo mount -o bind /proc /mnt/Jaunty-64-root/proc
sudo mount -o bind /dev /mnt/Jaunty-64-root/dev
sudo mount -o bind /dev/pts /mnt/Jaunty-64-root/dev/pts
sudo mount -o bind /sys /mnt/Jaunty-64-root/sys
sudo cp /etc/resolv.conf /mnt/Jaunty-64-root/etc/resolve.conf
sudo chroot /mnt/Jaunty-64-root /bin/bash

fi

```
It is easier if the partitions are labeled.  Just edit to your needs.  You will want to comment out the first line after the first use as the mount point will be in your /mnt directory.

This puts you in as root on that partition.  The "sudo cp /etc/resolv.conf /mnt/Jaunty-64-root/etc/resolve.conf" line gets you connected.  If you are not connected check that file and see if it is populated.

Mine in looks like;
```

# Generated by NetworkManager
nameserver 10.0.0.2

```
You can swipe the nameserver bit from some other install on your box if it is missing.  I just learned that this round.

You can also run the sudo lines in the script, one at a time in terminal.

You need to make sure that the permissions on the gedit file of the script are set to make it executable.  Like the scripts in /etc/grub.d.

You can run apt.  You can update-grub (or burg) and grub-install, grub-mkconfig, etc.  Any thing you do on an OS through terminal.

Real handy when you have an install that won't boot for a couple of weeks.

I upgraded a 8.04.4 install to 10.04 in a chroot environment yesterday.

---

### Post by purplefuku on 2010-02-08
I'm fairly certain I did the chroot right the first go around, but maybe I missed a step? I thought I bound everything required and whatnot, too... Ah well. I'll give it another shot when I get back home.

---

### Post by zet120 on 2010-02-09
Hi, 
How do I add an icon included in the system 40_custom?
Example:
[[img]http://dl.dropbox.com/u/3739707/Rozne/mb.png[/img]](http://dl.dropbox.com/u/3739707/Rozne/db.png)
top
Ubuntu GNU/Linux, with Linux... the effect of **/etc/burg.d/10_linux**  - presence icon

Mac OS X (32-bit)...
Mac OS X (64-bit)...
Windows 7 (loader)... the effect of **/etc/burg.d/30_os-prober** - presence icon

Windows 7...
Chameleon MacOS X... the effect of **/etc/burg.d/40_custom** - no icon!

There is a possibility?

---

### Post by richlyn9 on 2010-02-11
**purplefuku ** were you able to chroot and reinstal grub?

i am unable to connect to internet without my installed ubuntu and need to use a live cd so am facing difficulties....

---

### Post by cecilpierce on 2010-02-11
> **zet120 said:**
> Hi, 
How do I add an icon included in the system 40_custom?
Example:
[[img]http://dl.dropbox.com/u/3739707/Rozne/mb.png[/img]](http://dl.dropbox.com/u/3739707/Rozne/db.png)
top
Ubuntu GNU/Linux, with Linux... the effect of **/etc/burg.d/10_linux**  - presence icon

Mac OS X (32-bit)...
Mac OS X (64-bit)...
Windows 7 (loader)... the effect of **/etc/burg.d/30_os-prober** - presence icon

Windows 7...
Chameleon MacOS X... the effect of **/etc/burg.d/40_custom** - no icon!

There is a possibility?

Re: Grub 2 Title Tweaks Thread # 26

ranch hand came up with this awhile back, make a
 06_custom file in /etc/burg.d:

echo "Kubuntu 9.10 on sda22" >&2
cat << EOF
menuentry "Kubuntu 9.10 on sda22" --class (icon name) {
        set root=(hd0,22)
        linux /vmlinuz root=/dev/sda22 so quiet splash
        initrd /initrd.img
}
EOF

icon names in /boot/burg/themes/icons/large (or small)

---

### Post by zet120 on 2010-02-12
Hmmmm..
I did file **/etc/burg.d/06_custom**
```

echo "Windows 7 on sda3" >&2
cat << EOF
menuentry "Windows 7" --class (/boot/burg/themes/icons/large){
insmod ntfs
set root=(hd0,3)
search --no-floppy --fs-uuid --set 42f4bcb9f4bcb111
chainloader +1
}
EOF

```

effect

[img]http://dl.dropbox.com/u/3739707/Rozne/1.png[/img]

no icon. :(

---

### Post by ranch hand on 2010-02-12
Why not find the icon being used and change it?  Just change the image and leave the name the same and it should come up.

---

### Post by cecilpierce on 2010-02-13
Here is the windows part of my 06_custom file:

echo "Win XP a1" >&2
cat << EOF
menuentry "Win XP a1" --class Windows {
    set root=(hd0,1)
    chainloader +1
}

Thuis is ubuntu2 theme.

---

### Post by cecilpierce on 2010-02-13
This is what the "proto" theme looks like, you should have on the first line:

menuentry "Win XP a1" --class Windows {

---

### Post by richlyn9 on 2010-02-13
i am still trying to recover my ubuntu installs after last weeks update.
just to give you an idea..
my karmic / is on hda10
lucid / is on  hda09
and my dedicated Burg install is on hda11

i am trying to chroot in to my karmic install and reinstall burg on my MBR.

i did this 
[B]custom@custom:~$ sudo mount /dev/sda10 /mnt
custom@custom:~$ sudo mount /dev/sda11 /mnt
custom@custom:~$ sudo mount /dev/sda11 /mnt/boot
custom@custom:~$ sudo mount /dev/sda11 /mnt/boot/Burg
mount: mount point /mnt/boot/Burg does not exist
custom@custom:~$ sudo mount /dev/sda11 /mnt/Burg
mount: mount point /mnt/Burg does not exist
custom@custom:~$ sudo burg-install
sudo: burg-install: command not found
custom@custom:~$ mount /dev/sda10 /media/ubuntu
mount: only root can do that
custom@custom:~$ sudo mount /dev/sda10 /media/ubuntu
mount: mount point /media/ubuntu does not exist
custom@custom:~$ sudo mount /dev/hda3 /media/ubuntu/boot
mount: mount point /media/ubuntu/boot does not exist
custom@custom:~$ sudo mount /dev/hda11 /media/ubuntu/boot
mount: mount point /media/ubuntu/boot does not exist
custom@custom:~$ sudo mount /dev/hda11 /media/Burg/boot
mount: mount point /media/Burg/boot does not exist
custom@custom:~$ sudo mount /dev/hda11 /media/Burg
mount: mount point /media/Burg does not exist
custom@custom:~$ sudo mount /dev/hda11 /media/boot/Burg
mount: mount point /media/boot/Burg does not exist
custom@custom:~$ sudo mount /dev/hda11 /Burg/boot
mount: mount point /Burg/boot does not exist
custom@custom:~$ sudo mount /dev/hda11 /Burg
mount: mount point /Burg does not exist
custom@custom:~$ sudo mount /dev/hda11 /media/Burg
mount: mount point /media/Burg does not exist
custom@custom:~$ [/B]



some how it didnt go right
whats wrong

i am trying something similar to the following which i found after googling

[I][COLOR="Indigo"]mount /dev/sda10 /media/ubuntu
mount /dev/hda3 /media/ubuntu/boot
mount -t proc none /media/ubuntu/proc
mount -o bind /dev /media/ubuntu/d[/COLOR][/I]

---

### Post by cecilpierce on 2010-02-13
If burg is on sda11 seems like you were doing it on the sda10, anyhow ive messed mine up a few times, heres all I do, my burg is on sda1.

sudo mount /dev/sda1 /mnt
sudo mount -o bind /dev /mnt/dev
chroot /mnt
burg-install /dev/sda1
exit

your first line should be sda11 if thats where you have burg, good luck.

---

### Post by richlyn9 on 2010-02-14
> **cecilpierce said:**
> If burg is on sda11 seems like you were doing it on the sda10, anyhow ive messed mine up a few times, heres all I do, my burg is on sda1.

sudo mount /dev/sda1 /mnt
sudo mount -o bind /dev /mnt/dev
chroot /mnt
burg-install /dev/sda1
exit



I tried that but it gave an error...


[COLOR="SlateGray"]custom@custom:~$ sudo mount /dev/sda10 /mnt
custom@custom:~$ sudo mount -o bind /dev /mnt/dev
custom@custom:~$ chroot/mnt
bash: chroot/mnt: No such file or directory
custom@custom:~$ chroot /mnt
chroot: cannot change root directory to /mnt: Operation not permitted
custom@custom:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error
custom@custom:~$[/COLOR] 

*BTY sda11 has the dedicated Burg partition and sda10 has the stable karmic install and  sda9 has the testing lucid install.*

---

### Post by richlyn9 on 2010-02-17
i tried the following again


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

custom@custom:~$ sudo mount /dev/sd10 /media/ubuntu
mount: mount point /media/ubuntu does not exist
custom@custom:~$ sudo mount /dev/sd10 /mnt
mount: special device /dev/sd10 does not exist
custom@custom:~$ sudo mount/dev/sd10 /media/ubuntu
sudo: mount/dev/sd10: command not found
custom@custom:~$ sudo mount /dev/sda11 /mnt
custom@custom:~$ sudo mount -o bind /dev/mnt/dev
mount: can't find /dev/mnt/dev in /etc/fstab or /etc/mtab
custom@custom:~$ sudo mount -o bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
custom@custom:~$ sudo mount /dev/sda10 /mnt/boot
custom@custom:~$ sudo chroot /mnt/boot
chroot: cannot run command `/bin/bash': Exec format error
custom@custom:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
custom@custom:~$ cd /dev/sda11
bash: cd: /dev/sda11: Not a directory
custom@custom:~$ burg-install --root-directory=/media/boot/ /dev/sda11
bash: burg-install: command not found
custom@custom:~$ chroot /mnt
chroot: cannot change root directory to /mnt: Operation not permitted
custom@custom:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
custom@custom:~$


why does it give me
"**chroot: cannot run command `/bin/bash': Exec format error**"  and 
"**chroot: cannot run command `/bin/bash': No such file or directory**"  error?

an fdick -l  also comes back
custom@custom:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb
custom@custom:~$

---

### Post by popat007 on 2010-02-17
```
chroot /mnt
```

Try to run as sudo chroot /mnt

---

### Post by ranch hand on 2010-02-17
Do you have your partitions labeled?  If not the "ubuntu" entry will not make any sense to you bash.

Have you checked your /bin to see if there is a /bash?  There are other possibilities.

---

### Post by richlyn9 on 2010-02-17
> **popat007 said:**
> ```
chroot /mnt
```

Try to run as sudo chroot /mnt


i tried that it gives an error
[B]custom@custom:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory[/B]

---

### Post by richlyn9 on 2010-02-17
> **ranch hand said:**
> Do you have your partitions labeled?  If not the "ubuntu" entry will not make any sense to you bash.

Have you checked your /bin to see if there is a /bash?  There are other possibilities.

Yes the sda11 which is a dedicated Burg partition is labeled “Burg”
And the sda10 which has Karmic installed has no label
So should my code run as 
[I]sudo mount /dev/sd10 /media/karmic
sudo mount /dev/sd11 /Burg/boot[/I]
I have no clue about the /bin or /bash please guide

---

### Post by cecilpierce on 2010-02-17
> **richlyn9 said:**
> Yes the sda11 which is a dedicated Burg partition is labeled “Burg”
And the sda10 which has Karmic installed has no label
So should my code run as 
[I]sudo mount /dev/sd10 /media/karmic
sudo mount /dev/sd11 /Burg/boot[/I]
I have no clue about the /bin or /bash please guide

Your in a mell of a hess ! sorry.
can you boot to the sda11, your typing /dev/sd11, if you can goto terminal and do sudo burg-install /dev/sda.
chroot is in: /usr/sbin/chroot
sh is in: /bin/sh
you can see if they are install by typing: whereis sh or chroot.
Wish I knew more to help but I'm having problems to !

---

### Post by cecilpierce on 2010-02-17
richlyn9 did you try:

sudo mount /dev/sda11 /mnt
sudo mount -o bind /dev /mnt/dev
sudo chroot /mnt
sudo burg-install /dev/sda

in ctrl+alt+F1 terminal ?

It has always worked for me.

---

### Post by ranch hand on 2010-02-17
> **richlyn9 said:**
> Yes the sda11 which is a dedicated Burg partition is labeled “Burg”
And the sda10 which has Karmic installed has no label
So should my code run as 
[I]sudo mount /dev/sd10 /media/karmic
sudo mount /dev/sd11 /Burg/boot[/I]
I have no clue about the /bin or /bash please guide
Go to Placed>Home Folder.

Click on "File System"

Click on "bin"

You should have a list display or an icon display in alpha-numeric order so "bash" should be right up there toward the top somewhere.

If it is not check to see if "dash" is in there.

---

### Post by richlyn9 on 2010-02-18
> **cecilpierce said:**
> richlyn9 did you try:

sudo mount /dev/sda11 /mnt
sudo mount -o bind /dev /mnt/dev
sudo chroot /mnt
sudo burg-install /dev/sda

in ctrl+alt+F1 terminal ?

It has always worked for me.

it gave me an error: cant find /mnt/dev in etc/fstab....

[B]custom@custom:~$ whereis sh
sh: /bin/sh /bin/sh.distrib /usr/share/man/man1/sh.1.gz
custom@custom:~$ whereis chroot
chroot: /usr/sbin/chroot /usr/share/man/man8/chroot.8.gz
custom@custom:~$ sudo mount /dev/sda10 /mnt
custom@custom:~$ sudo mount -o bind/dev /mnt/dev
[COLOR="Navy"]mount: can't find /mnt/dev in /etc/fstab or /etc/mtab[/COLOR]
custom@custom:~$ sudo chroot /mnt
[/B]

---

### Post by richlyn9 on 2010-02-18
> **ranch hand said:**
> Go to Placed>Home Folder.

Click on "File System"

Click on "bin"

You should have a list display or an icon display in alpha-numeric order so "bash" should be right up there toward the top somewhere.

If it is not check to see if "dash" is in there.

it is there

[I]custom@custom:~$ whereis sh
sh: /bin/sh /bin/sh.distrib /usr/share/man/man1/sh.1.gz
custom@custom:~$ whereis chroot
chroot: /usr/sbin/chroot /usr/share/man/man8/chroot.8.gz
custom@custom:~$ whereis dash
dash: /bin/dash /usr/share/man/man1/dash.1.gz[/I]

---

### Post by richlyn9 on 2010-02-18
i ran a fdisk

custom@custom:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa64ca64c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        5099    20474842+   7  HPFS/NTFS
/dev/sda3            5100       19457   115330635    f  W95 Ext'd (LBA)
/dev/sda5            5100        8953    30957223+   7  HPFS/NTFS
/dev/sda6            8954       12809    30973288+   7  HPFS/NTFS
/dev/sda7           12810       16633    30716248+   7  HPFS/NTFS
/dev/sda8           16634       16764     1052226   82  Linux swap / Solaris
/dev/sda9           16765       18110    10811713+  83  Linux
/dev/sda10          18111       19325     9759456   83  Linux
/dev/sda11          19326       19457     1060258+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae1f8566

---

### Post by richlyn9 on 2010-02-18
i tried a slightly different code
with little sucess

custom@custom:~$ sudo mount /dev/sda10 /mnt
mount: /dev/sda10 already mounted or /mnt busy
mount: according to mtab, /dev/sda10 is already mounted on /mnt
custom@custom:~$ sudo mount --bind /dev /mnt/dev
custom@custom:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error
custom@custom:~$

---

### Post by ranch hand on 2010-02-18
> **richlyn9 said:**
> it is there

[I]custom@custom:~$ whereis sh
sh: /bin/sh /bin/sh.distrib /usr/share/man/man1/sh.1.gz
custom@custom:~$ whereis chroot
chroot: /usr/sbin/chroot /usr/share/man/man8/chroot.8.gz
custom@custom:~$ whereis dash
dash: /bin/dash /usr/share/man/man1/dash.1.gz[/I]
I do not see a mention of bash.  If that is the case bash is not going to work.

I am not familiar with dash (bash is new to me too).  I would look at the man page.

I would also just try substituting "dash" for "bash".  The little I understand about them seems to tell me that may just work.  I think they are very similar.

EDIT
I have both on here, have no idea why.  Make sure you check for "bash" to make sure it is there.  Your error messages suggest it is not.  If it is not you could also install it.

---

### Post by richlyn9 on 2010-02-19
> **ranch hand said:**
> I do not see a mention of bash.  If that is the case bash is not going to work.

I am not familiar with dash (bash is new to me too).  I would look at the man page.

I would also just try substituting "dash" for "bash".  The little I understand about them seems to tell me that may just work.  I think they are very similar.

EDIT
I have both on here, have no idea why.  Make sure you check for "bash" to make sure it is there.  Your error messages suggest it is not.  If it is not you could also install it.

yeah its there
[B]icustom@custom:~$ whereis bash
bash: /bin/bash /etc/bash.bashrc /usr/share/bash /usr/share/man/man1/bash.1.gz[/B]

---

### Post by richlyn9 on 2010-02-19
i think after two weeks i am running a blank.
I may have to reinstall the entire thing again....


sad  that i could'nt get this solved without reinstalling..:(

---

### Post by richlyn9 on 2010-02-22
[SIZE="4"][B][COLOR="Navy"]wwwwwwwwwwwwwwooooooooooooooooohhhhhhhoooooooooooo oooooooo
i Have done it.......
i have atlast been able to chroot !!!!!![/COLOR][/B][/SIZE]

I was mounting a wrong partition all the while...such an *** of me.
BTY any command to know which partition has what distro installed from Live cd?

---

### Post by richlyn9 on 2010-02-22
heres what i did............


custom@custom:~$ fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb

Disk /dev/sdc: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001a359

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         488     3919828+   b  W95 FAT32
custom@custom:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa64ca64c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        5099    20474842+   7  HPFS/NTFS
/dev/sda3            5100       19457   115330635    f  W95 Ext'd (LBA)
/dev/sda5            5100        8953    30957223+   7  HPFS/NTFS
/dev/sda6            8954       12809    30973288+   7  HPFS/NTFS
/dev/sda7           12810       16633    30716248+   7  HPFS/NTFS
/dev/sda8           16634       16764     1052226   82  Linux swap / Solaris
/dev/sda9           16765       18110    10811713+  83  Linux
/dev/sda10          18111       19325     9759456   83  Linux
/dev/sda11          19326       19457     1060258+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae1f8566

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       31871   256003776   83  Linux
/dev/sdb2           31872       60801   232380225   83  Linux

Disk /dev/sdc: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001a359

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         488     3919828+   b  W95 FAT32
custom@custom:~$ sudo mount /dev/sda9 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@custom:/# dpkg-divert --local --rename --add /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@custom:/# ln -s /bin/true /sbin/initctl 
root@custom:/# sudo burg-install --root-directory=/mnt/ /dev/sd11
sudo: unable to resolve host custom
/usr/sbin/burg-probe: error: cannot stat `/dev/sd11'.
Invalid device `/dev/sd11'.
Try `/usr/sbin/burg-setup --help' for more information.
[COLOR="Navy"]"I manually mounted the dedicated Burg partition "[/COLOR]
root@custom:/# sudo burg-install --root-directory=/mnt/ /dev/sd11
sudo: unable to resolve host custom
/usr/sbin/burg-probe: error: cannot stat `/dev/sd11'.
Invalid device `/dev/sd11'.
Try `/usr/sbin/burg-setup --help' for more information.
root@custom:/# update-burg
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
Found Microsoft Windows XP Professional on /dev/sda1
done
root@custom:/# lsb_release -a 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
root@custom:/# uname -m
i686
root@custom:/# sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
sudo: unable to resolve host custom
umount: /mnt/dev/pts: not found
root@custom:/# exit
exit
custom@custom:~$ lsb_release -a 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
custom@custom:~$

---

### Post by richlyn9 on 2010-02-22
root@custom:/# sudo burg-install --root-directory=/mnt/ /dev/sd11
sudo: unable to resolve host custom
/usr/sbin/burg-probe: error: cannot stat `/dev/sd11'.
Invalid device `/dev/sd11'.
Try `/usr/sbin/burg-setup --help' for more information.
"I manually mounted the dedicated Burg partition "
root@custom:/# sudo burg-install --root-directory=/mnt/ /dev/sd11
sudo: unable to resolve host custom
/usr/sbin/burg-probe: error: cannot stat `/dev/sd11'.
Invalid device `/dev/sd11'.
Try `/usr/sbin/burg-setup --help' for more information.
root@custom:/# update-burg
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
Found Microsoft Windows XP Professional on /dev/sda1
done



[I][COLOR="Navy"]i am able to chroot to karmic existing install
however i am not able to install Burg on the MBR or the dedicated partition
or rather the update-burg does not find my existing ubuntu installs
what can the matter be?

what am i doing wrong[/COLOR][/I]

---

### Post by BwackNinja on 2010-02-22
try: sudo burg-install --root-directory=/mnt/ /dev/sd**a**11

---

### Post by setherd on 2010-02-22
ISn't burg supposed to update it's self when a new kernel is added?
I seem to recall that was it's previous behavior.
I noticed tonight I was still running 2.6.32-12 when I had just  installed 2.6.32-14 earlier today.

turns out burg isn't updating it's self when  new kernel is installed. a  simple "sudo update-burg" solved it.
I seem to recall burg used to have some link that when update grub was  done it also did update-burg.
am I the only one with this issue?

---

### Post by ranch hand on 2010-02-22
The best way to avoid that hassle is to use custom entries that are "symbolic" and just call for the partition.  They never need updated, ever.  You can change the Debian based OS on the partition and the entry will work with out editing.  Just boots the newest kernel on the partition.

---

### Post by Starks on 2010-02-22
richlyn9, you were having problems because you weren't chrooting properly.

[http://ubuntuforums.org/showthread.php?t=1326721](http://ubuntuforums.org/showthread.php?t=1326721)

---

### Post by richlyn9 on 2010-02-22
> **Starks said:**
> richlyn9, you were having problems because you weren't chrooting properly.

[http://ubuntuforums.org/showthread.php?t=1326721](http://ubuntuforums.org/showthread.php?t=1326721)

Do you meant to sya that the chroot that i am able to do is not correct???

---

### Post by Starks on 2010-02-22
It works, but it is not the best procedure anymore.

---

### Post by richlyn9 on 2010-02-24
i tried that again
it gave me another error this time

root@custom:/# burg-install --root-directory=/mnt/ /dev/sda11
/usr/sbin/burg-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/burg-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/burg-setup: error: if you really want blocklists, use --force.
root@custom:/# sudo burg-install --root-directory=/mnt/ /dev/sda11
sudo: unable to resolve host custom
/usr/sbin/burg-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/burg-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/burg-setup: error: if you really want blocklists, use --force.
root@custom:/# burg-install --root-directory=/mnt/ /dev/sda11
/usr/sbin/burg-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/burg-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/burg-setup: error: if you really want blocklists, use --force.
root@custom:/# sudo burg-install "(sda11)"
sudo: unable to resolve host custom
/usr/sbin/burg-setup: error: no mapping exists for `sda11'.

---

### Post by ranch hand on 2010-02-24
Why are you trying to install on a partition?  This really is a bad idea.

The command you are looking for is "(hd0,11)".  I do not endorse using it.

---

### Post by richlyn9 on 2010-02-24
i tried this and it dedected by lucid testing  install but not the karmic install in which i am chrooted into

root@custom:/# sudo update-burg
sudo: unable to resolve host custom
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu lucid (development branch) (10.04) on /dev/sda10
done
root@custom:/#

---

### Post by richlyn9 on 2010-02-24
> **ranch hand said:**
> Why are you trying to install on a partition?  This really is a bad idea.

The command you are looking for is "(hd0,11)".  I do not endorse using it.

so to be safer should i just run this 
sudo burg-install /dev/sda

---

### Post by richlyn9 on 2010-02-24
> **ranch hand said:**
> Why are you trying to install on a partition?  This really is a bad idea.

The command you are looking for is "(hd0,11)".  I do not endorse using it.

i chrootes into my karmic install and ran 

root@custom:/# sudo burg-install --force --root-directory=/media/Burg /dev/sda11
and then ran 
root@custom:/# sudo update-burg


it didnt find the karmic install however that i am chroot into

---

### Post by ranch hand on 2010-02-24
> **richlyn9 said:**
> so to be safer should i just run this 
sudo burg-install /dev/sda
Yes.

---

### Post by Starks on 2010-02-24
How does one wipe burg completely from the boot-up process?

---

### Post by ranch hand on 2010-02-24
```

sudo grub-install /dev/sda

```
should put grub right back to work for you.

---

### Post by richlyn9 on 2010-02-25
its done.....


root@custom:/# burg-install --force --root-directory=/mnt/ /dev/sda11


root@custom:/# sudo update-burg
sudo: unable to resolve host custom
Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
ls: cannot access /media/disk: No such file or directory
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu lucid (development branch) (10.04) on /dev/sda10
done
root@custom:/#


though i didnt find the karmic install...
after rebooting it did show up the karmic kernels and was able to boot in to Karmic install.
Now everything is working fine as before



i admit i was a bit adamant on installing Burg and that to a dedicated partition by chroot, but its a good experience learning chroot and worth the wait!!!


Thanks ranchhand bean123 vishalrao starks and cecilpierce for your help
and guidance

---

### Post by ranch hand on 2010-02-25
Probably should mark this thread as solved (top of page under "thread tools").

chroot is FUN.

I am doing a apt-get dist-upgrade of 8.04 to 10.04 (attempting to anyway) right now from another drive.

---

### Post by shafin on 2010-03-05
With ubuntu's new branding, BURG needed a new theme, so I took some hours to dig at sora's code and come out with something. With this, the boot gets a much more unified feel.

I tried to base this theme on ubuntu's new branding and the notification pop-ups. 
[http://gnome-look.org/content/show.php?content=121105](http://gnome-look.org/content/show.php?content=121105)

---

### Post by dyltman on 2010-03-05
> **shafin said:**
> With ubuntu's new branding, BURG needed a new theme, so I took some hours to dig at sora's code and come out with something. With this, the boot gets a much more unified feel.

I tried to base this theme on ubuntu's new branding and the notification pop-ups. 
[http://gnome-look.org/content/show.php?content=121105](http://gnome-look.org/content/show.php?content=121105)

That's awesome!

---

### Post by andrewthomas on 2010-03-08
I'm working with the sora theme and cannot get my user defined selected icons to increase in size like the stock ones do.  For instance, when you are selecting the Ubuntu logo, it increases in size maybe 20%.  I copied icons for LinuxMint and Fedora from the /boot/burg/themes/icons folder to the /boot/burg/themes/sora/icons folder.  I scaled them down and made a larger size color hover icon and a smaller gray regular icon to match the other entries in the folder ( I also put two identical sized ones in the icons-nopop folder for good measure.)  When my icons are selected, they change from gray to color, yet they don't increase in size.  Any ideas why?

---

### Post by ranch hand on 2010-03-08
Unless you changed the name to an existing one in Sora you probably need to add them to the script somewhere.  I do not have that file handy to look at as it is on a different OS.

I do not fool with it much as it does not play nice with my custom menu entries and I like never having to update the entries.

---

### Post by andrewthomas on 2010-03-09
> **andrewthomas said:**
>   When my icons are selected, they change from gray to color, yet they don't increase in size.  Any ideas why?
I found the problem.  I didn't realize that the hover icon for x (button-x-hover.png) needed to be the same size as the regular icon for x (button-x.png.)  Once I centered the scaled down image in a same size canvas with gimp, it is working as it was intended.

---

### Post by bean123 on 2010-03-09
hi guys, I'm back from my vacation, and start some coding, :)

New package: burg 1.98+20100309-1 and burg-themes 1.98+20100309-1

It syncs with grub r2249, aka grub 1.98 release a few days ago. Now it support both the burg and grub theme. To try grub theme, set GRUB_THEME to the name of the theme file. For example:

```

GRUB_THEME=/boot/burg/themes/debian-theme/theme.txt

```

And run update-burg. 

Although it has some obvious bugs, for example, use c to open a terminal and enter some command until screen scrolls. And it pops a black windows when booting ...

BTW, as grub theme uses all lowercase letter for OS label, I has changed burg-themes to use the same naming conversion as well.

---

### Post by bean123 on 2010-03-09
> **shafin said:**
> With ubuntu's new branding, BURG needed a new theme, so I took some hours to dig at sora's code and come out with something. With this, the boot gets a much more unified feel.

I tried to base this theme on ubuntu's new branding and the notification pop-ups. 
[http://gnome-look.org/content/show.php?content=121105](http://gnome-look.org/content/show.php?content=121105)

Oh it looks great, thanks a lot for your work ! Would you mind if I add it to burg-themes ?

---

### Post by Starks on 2010-03-10
Still can't get Plymouth to work with BURG.

---

### Post by bean123 on 2010-03-10
> **Starks said:**
> Still can't get Plymouth to work with BURG.

Strange, burg should has the same effect as grub2. Does the grub2 experimental package from Felix's ppa work ?

---

### Post by cecilpierce on 2010-03-10
bean123,
Is the save function still work when you hit 't' to change the theme ? Also I can't get the debian theme to come up, Thanks, Cecil

---

### Post by bean123 on 2010-03-11
> **cecilpierce said:**
> bean123,
Is the save function still work when you hit 't' to change the theme ? Also I can't get the debian theme to come up, Thanks, Cecil

Yes, it should still works for burg themes, but grub theme hasn't implemented this function yet.

Oh I make a mistake previously, the path to debian theme is actually:
```

GRUB_THEME=/boot/burg/themes/debian-theme/theme.txt

```

---

### Post by Starks on 2010-03-11
> **bean123 said:**
> Strange, burg should has the same effect as grub2. Does the grub2 experimental package from Felix's ppa work ?
Felix's PPA breaks GRUB these days. When it worked, I remember it not breaking Plymouth.

---

### Post by shafin on 2010-03-11
> **bean123 said:**
> Oh it looks great, thanks a lot for your work ! Would you mind if I add it to burg-themes ?
Please go ahead :)
The package here is a bit outdated, gnome-look page contains the updated theme.

---

### Post by cecilpierce on 2010-03-12
> **bean123 said:**
> Yes, it should still works for burg themes, but grub theme hasn't implemented this function yet.

Oh I make a mistake previously, the path to debian theme is actually:
```

GRUB_THEME=/boot/burg/themes/debian-theme/theme.txt

```

When I put this in I get a plain gray and white grub menu, if I comment it out it works ok.
also something went wrong with the burg update and it put me in grub rescue so I removed all and reinstalled all and got the same rescue so I looked at burg on another hard drive and found /etc/default/burg was missing so I copied it over and now its working !!! Any ideas what I messed up ?

heres a snap shot of the error msg, Thanks, Cecil

---

### Post by bean123 on 2010-03-17
> **Starks said:**
> Still can't get Plymouth to work with BURG.

I did some tests today, this is actually a configuration issue. Open /etc/default/burg, change

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet"

```

to

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```

And run update-burg, that should do it. I'd change the default value in the next version.

---

### Post by bean123 on 2010-03-17
> **cecilpierce said:**
> When I put this in I get a plain gray and white grub menu, if I comment it out it works ok.
also something went wrong with the burg update and it put me in grub rescue so I removed all and reinstalled all and got the same rescue so I looked at burg on another hard drive and found /etc/default/burg was missing so I copied it over and now its working !!! Any ideas what I messed up ?

heres a snap shot of the error msg, Thanks, Cecil

It seems to be all right for me. Perhaps you can check if burg and burg-themes are both at the latest version 20100309-1 ?

If it still doesn't work, please paste the generate burg.cfg.

---

### Post by cecilpierce on 2010-03-17
I checked all the burg files they are 20100309-1.
I have the debian-theme in /boot/burg/themes it has a file 'theme.txt' and all the rest of the themes just have 'theme' ?
Here is my cfg, thanks

---

### Post by cecilpierce on 2010-03-17
burg.cfg didnt upload !

---

### Post by cecilpierce on 2010-03-17
try again
I get this:
Upload Errors
burg.cfg:
Invalid File
Dont know whats going on ?

---

### Post by cecilpierce on 2010-03-17
Sorry, this is the best I can do with copy-paste>

### BEGIN /etc/burg.d/00_header ###
set theme_name=ubuntu
if [ -s $prefix/burgenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu
    load_config ${prefix}/themes/${theme_name}/theme
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme
  insmod vbe
  insmod png
  insmod jpeg
  set gfxmode=640x480
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  controller.ext
fi
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 9c393deb-7d00-466c-827b-0e6e767921d2
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=15
### END /etc/burg.d/00_header ###

---

### Post by bean123 on 2010-03-17
> **cecilpierce said:**
> try again
I get this:
Upload Errors
burg.cfg:
Invalid File
Dont know whats going on ?

It doesn't allow .cfg extension, you can zip or gz it first.

Anyway, from the output, it seems to be the same as burg theme, has you forgot to run update-burg ? BTW, please paste your /etc/default/burg also.

---

### Post by cecilpierce on 2010-03-17
> **bean123 said:**
> It doesn't allow .cfg extension, you can zip or gz it first.

Anyway, from the output, it seems to be the same as burg theme, has you forgot to run update-burg ? BTW, please paste your /etc/default/burg also.

Thanks for that info.
the debian-theme doesn't show in the burg.cfg after I did update-burg.

---

### Post by bean123 on 2010-03-17
> **cecilpierce said:**
> Thanks for that info.
the debian-theme doesn't show in the burg.cfg after I did update-burg.

But in your /etc/default/burg, GRUB_THEME is set to saved and 
/boot/burg/themes/debian-theme/theme.txt is commented out, could you please swap the setting and run update-burg again to generate a new burg.cfg ?

---

### Post by cecilpierce on 2010-03-17
Did that and heres what I get, same as before.

---

### Post by bean123 on 2010-03-17
> **cecilpierce said:**
> Did that and heres what I get, same as before.

Could you post the generated burg.cfg file ?

---

### Post by Starks on 2010-03-17
bean, shouldn't the burg dummy package install the themes and emulator?

---

### Post by cecilpierce on 2010-03-17
> **bean123 said:**
> Could you post the generated burg.cfg file ?

here is the updated burg.cfg after editing /etc/default/burg.

---

### Post by cecilpierce on 2010-03-17
bean123,
I just did update-burg, rebooted and the debian-theme came up but its very slow and jerky. The 't' function doesn't work, is it suppose to ?
Burg-emu won't show it, think I will switch back unless you have a solution. Thanks for the help.

---

### Post by bean123 on 2010-03-18
> **cecilpierce said:**
> bean123,
I just did update-burg, rebooted and the debian-theme came up but its very slow and jerky. The 't' function doesn't work, is it suppose to ?

Yeah, it's supposed to, that's bugs from grub. In fact, I can list a few more, for example, the console mode windows would go crazy if you have more than one screen of output. As for 't' and 'f' function, it hasn't been implemented yet.

> Burg-emu won't show it, think I will switch back unless you have a solution. Thanks for the help.

Oh I see, you mean burg-emu. It's probably because burg.cfg uses some function not included in burg-emu, it should be easy to fix. I normally test it in virtualbox so I don't notice it.

---

### Post by bean123 on 2010-03-18
> **Starks said:**
> bean, shouldn't the burg dummy package install the themes and emulator?

Good idea, I would change it in the next version. BTW, is plymouth working with the new "splash" option ?

---

### Post by Starks on 2010-03-18
It works fine on shutdown.

Startup is a different animal. GRUB screen remains for a few seconds after selection as the boot continues. Plymouth may flash for a split-second at a non-KMS resolution.

---

### Post by bean123 on 2010-03-18
> **Starks said:**
> It works fine on shutdown.

Startup is a different animal. GRUB screen remains for a few seconds after selection as the boot continues. Plymouth may flash for a split-second at a non-KMS resolution.

What about the official grub2, does it have the same issue ?

---

### Post by ranch hand on 2010-03-18
Neither grub nor burg is the problem here, this is a plymouth "issue".

---

### Post by Starks on 2010-03-18
> **bean123 said:**
> What about the official grub2, does it have the same issue ?
Nope. Works fine.

---

### Post by bean123 on 2010-03-18
> **Starks said:**
> Nope. Works fine.

I'm a little confused, is this a problem of plymouth or not. BTW, what's the version of grub2 that works fine ?

---

### Post by Starks on 2010-03-18
Whichever version that's the latest in lucid main.

---

### Post by bean123 on 2010-03-18
> **cecilpierce said:**
> bean123,
Burg-emu won't show it, think I will switch back unless you have a solution. Thanks for the help.

Oh, I know what's wrong with burg-emu. grub uses absolute path to locate font file, so it needs to access disk directly. I have disabled disk access by default, you need to use option -D to enable it:

```

sudo burg-emu -D

```

---

### Post by bean123 on 2010-03-18
> **Starks said:**
> Whichever version that's the latest in lucid main.

I have installed a new lucid from scratch from network to ensure all package are the latest version:

grub-pc - 1.98-1ubuntu1
burg-pc - 1.98+20100309-1+lucid
plymouth - 0.8.0~-12

plymouth-set-default-theme is set to ubuntu-logo. From what I can gather, grub and burg behaves the same, there is some text appear before the logo shows up.

Although there is a small difference in video mode switching, it has to do with the GRUB_GFXPAYLOAD_LINUX option, grub uses "text" by default, which means switch back to text mode just before booting, while burg uses "keep" by default, which means keep the current screen resolution. IMO burg's default value is more sound. You can try both settings to see the difference.

---

### Post by phen0m on 2010-03-21
Awww my baby is growing!  
Proud daddy of Sora.

---

### Post by bean123 on 2010-03-21
> **phen0m said:**
> Awww my baby is growing!  
Proud daddy of Sora.

Oh, are you the author of Sora ? Thanks a lot for the great work.

BTW, would you mind adding more icons for Sora ? I have found a lot of large/small icons for other themes, but Sora uses hover and grey icon, it needs to be handled differently.

---

### Post by bean123 on 2010-03-21
New package 1.98+20100322-1:

* meta package burg depends on burg-pc, burg-emu and burg-themes, so you can use it to install all components.

* add theme radiance by shafin, the original url is:
[http://gnome-look.org/content/show.php?content=121105](http://gnome-look.org/content/show.php?content=121105)

* many improvement for UEFI/EFI platform
With this version, I can quadruple boot Windows 7, OSX, Ubuntu Lucid and FreeBSD 8 on GPT disk on UEFI/Apple EFI/PCBIOS machine. Although it is a little off topic here, I'd write a new thread for the howto.

---

### Post by Owen.C93 on 2010-03-21
For some reason anything but the sora theme just resorts to the text grub menu.

---

### Post by bean123 on 2010-03-22
> **Owen.C93 said:**
> For some reason anything but the sora theme just resorts to the text grub menu.

It's working fine here. Don't forget the burg-install plus update-burg step after you upgrade. If it still doesn't work, try purge and reinstall.

---

### Post by Chrigi on 2010-03-22
Hello

I set up BURG and it work's great :) but it doesn't honor the GRUB_DEFAULT="Windows 7 (loader) (on /dev/sda1)" in /etc/default/burg
Do I have to set this on a per theme basis? How?
I mostly boot into Windows and then it's way more convenient when it's set so by default.

---

### Post by bean123 on 2010-03-22
> **Chrigi said:**
> Hello

I set up BURG and it work's great :) but it doesn't honor the GRUB_DEFAULT="Windows 7 (loader) (on /dev/sda1)" in /etc/default/burg
Do I have to set this on a per theme basis? How?
I mostly boot into Windows and then it's way more convenient when it's set so by default.

You can use menu index (0 based), for example:

GRUB_DEFAULT=1

Means use the second item as default. You can also use this:

GRUB_DEFAULT=saved

which means save the previous selection and use it as default.

---

### Post by Chrigi on 2010-03-23
@bean123
Thank you very much. Works great :)

---

### Post by Spox5 on 2010-03-25
How can I use both Usplash and Burg? 
What  should I do to Usplash work?

---

### Post by ranch hand on 2010-03-25
Usplash went out with 9.04.  9.10 used xsplash.

We are using plymouth.

There are a lot of threads on plymouth.  Use the "search this thread" tool to search for "plymouth".

---

### Post by bean123 on 2010-03-25
> **Spox5 said:**
> How can I use both Usplash and Burg? 
What  should I do to Usplash work?

Open /etc/default/burg, the value of GRUB_CMDLINE_LINUX_DEFAULT should be:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```

Previous version of burg miss the splash option, the latest one has added it. Although if you upgrade instead of fresh install, the previous setting will remain.

---

### Post by cheapsaket on 2010-03-25
Bean, do you have a wiki somewhere that lays out the steps to get burg up and running? 

thanks

---

### Post by bean123 on 2010-03-25
> **cheapsaket said:**
> Bean, do you have a wiki somewhere that lays out the steps to get burg up and running? 

thanks

Yeah, here:

[http://code.google.com/p/burg/w/list](http://code.google.com/p/burg/w/list)

---

### Post by Owen.C93 on 2010-03-25
Hmm still cant use any other themes apart from sora.

Pressing t at boot means I can use them all but editing the burg file just makes it result to text burg.

---

### Post by bean123 on 2010-03-26
> **Owen.C93 said:**
> Hmm still cant use any other themes apart from sora.

Pressing t at boot means I can use them all but editing the burg file just makes it result to text burg.

Could you paste the content of /etc/default/burg and /boot/burg/burg.cfg ?

---

### Post by richlyn9 on 2010-04-05
I have a update for burg showing up on update manager but I have burg on  a dedicated partition and would not want to mess up things. But I got thinking how to get the update manually(so that I know what I am doing)installed to my dedicated partition(how long shall I avoid it). 
So should I get install the update and install burg to dedicated partition like I did it the first time or should I try purge –remove  or reinstall the pakage(sice I don’t want to clutter my dedicated partition).
sudo apt-get remove 
sudo apt-get --purge remove 
Please advise how should I go about this.

---

### Post by richlyn9 on 2010-04-09
can I just run the update in the update manager and then run this
sudo burg-install --force --root-directory=/media/Burg /dev/**sda**
sudo burg-mkconfig -o /media/Burg/boot/burg/burg.cfg
I think it should work
Or else manually reinstall burg 
Sudo apt-get reinstall burg and then 
sudo burg-install --force --root-directory=/media/Burg /dev/**sda**
sudo burg-mkconfig -o /media/Burg/boot/burg/burg.cfg

i have made this up on the lines of hermans tutorials
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)

---

### Post by Owen.C93 on 2010-04-11
> **bean123 said:**
> Could you paste the content of /etc/default/burg and /boot/burg/burg.cfg ?
Sorry I completely forgot about this thread.

I got it working now, I think I forgot to run burg-install to update it.

---

### Post by Starks on 2010-04-11
bean, is there anyway to tie update-burg to update-grub?

I really dislike how I currently have to update them separately whenever I install a new kernel.

---

### Post by Troublegum on 2010-04-18
**@bean: **Thank you for your great work. BURG is really cool. 
But one thing bugs me. The option [FONT=Courier New]GRUB_DEFAULT=saved[/FONT] in [FONT=Courier New]/etc/default/burg[/FONT] is without effect.
Every time I reboot, the default entry is the first one, regardless which system I booted before. 

But [FONT=Courier New]GRUB_THEME=saved[/FONT] works, [FONT=Courier New]/boot/burg/burgenv[/FONT] gets updated with the last used theme. But it does not contain a [FONT=Courier New]saved_entry[/FONT] variable:
```
nam@grub2-test:~$ burg-editenv list
theme_name=ubuntu2
theme_fold=

```I compared the[FONT=Courier New] /etc/burg.d/00_header[/FONT] script to the [FONT=Courier New]/etc/grub.d/00_header[/FONT] script and the code that has to do with saving the last used entry is different. But even with the [FONT=Courier New]00_header[/FONT] script from [FONT=Courier New]grub.d[/FONT], it didnt work.

I'm running Ubuntu 9.10 with burg in version 1.98+20100322-1ubuntu1 (within Virtualbox on a Ubuntu 9.10 host). 

Can you help me on that?


@Starks: you could symlink update-grub to update-burg. That should work.

---

### Post by Podex on 2010-04-18
> **Troublegum said:**
> 
@Starks: you could symlink update-grub to update-burg. That should work.

Or just make an alias:

```
alias update-grub="sudo update-grub && sudo update-burg"
```

and put it in .bashrc

---

### Post by tokyobadger on 2010-04-18
I have a couple of questions and would be grateful for some input:

1) what's the correct GRUB2 syntax for adding FreeBSD and in which file should it reside (I'm also using BURG) - in GRUB Legacy it looks like this:
```
root (hd2,2a) 
kernel /boot/loader
```

2) my OS icons in BURG are 'confused' - I get Gentoo icons for Gentoo + Arch and vice-versa (the Arch icons are the outdated ones) - I used a universal /boot partition on /dev/sda until now which contained the kernels for the various distros (excluding Win7RC and FreeBSD) - now the /boot entry and the / partition for each is duplicated; Ubuntu is labeled with the correct icon consistently for each kernel 

3) Does GRUB2/BURG support 2560x1600 resolution? At the moment I think I'm still on a much lower resolution

4) (I know it's a Plymouth question and I should ask elsewhere) why does my Plymouth splash show 'checking disks for errors' at each boot since installing GRUB2/BURG?

All constructive feedback/input welcomed

---

### Post by bean123 on 2010-04-21
> **tokyobadger said:**
> I have a couple of questions and would be grateful for some input:

1) what's the correct GRUB2 syntax for adding FreeBSD and in which file should it reside (I'm also using BURG) - in GRUB Legacy it looks like this:
```
root (hd2,2a) 
kernel /boot/loader
```

There is two way to load FreeBSD, one is to use /boot/loader, the forth loader, another is to load the kernel directly. Here are the commands: (Partition name may be different, you can use "ls -l" to find out the correct one).

Forth loader:
```

set root=(hd2,2a)
kfreebsd /boot/loader

```

Direct load:
```

set root=(hd2,2a)
kfreebsd /boot/kernel/kernel
kfreebsd_loadenv /boot/devices.hint
set FreeBSD.vfs.root.mountfrom=ufs:/dev/ad0s1

```

> 
2) my OS icons in BURG are 'confused' - I get Gentoo icons for Gentoo + Arch and vice-versa (the Arch icons are the outdated ones) - I used a universal /boot partition on /dev/sda until now which contained the kernels for the various distros (excluding Win7RC and FreeBSD) - now the /boot entry and the / partition for each is duplicated; Ubuntu is labeled with the correct icon consistently for each kernel

This is mostly os-prober's fault. grub2 and burg relies on os-prober to detect OS properly.

> 
3) Does GRUB2/BURG support 2560x1600 resolution? At the moment I think I'm still on a much lower resolution

It depends on your video bios, use vbeinfo to find out what modes are supported.

> 
4) (I know it's a Plymouth question and I should ask elsewhere) why does my Plymouth splash show 'checking disks for errors' at each boot since installing GRUB2/BURG?

All constructive feedback/input welcomed
Sorry, I have no idea.

---

### Post by bean123 on 2010-04-21
BTW, I have just created a forum for BURG:

[http://www.burgloader.com/bbs/index.php](http://www.burgloader.com/bbs/index.php)

In the "BURG Themes" section, ingalex has posted a lot of new customized themes.

---

### Post by ranch hand on 2010-04-21
I think that to fine your partitions it would be more informative to use;
```

sudo sfdisk -l

```
I  believe that ls -l will give you the contents of your /home directory.

---

### Post by bean123 on 2010-04-21
> **Starks said:**
> bean, is there anyway to tie update-burg to update-grub?

I really dislike how I currently have to update them separately whenever I install a new kernel.

You can edit /etc/kernel-img.conf to let it run update-burg when you update your kernel.

---

### Post by Zach Thomas on 2010-04-21
Hey bean, BURG is great! I'm really new to Ubuntu and not the smartest with computers, so maybe this is a silly question. But I intend to upgrade to 10.04 from 9.10 at the end of this month and was wondering how BURG will be affected? Do I need to change anything? Again sorry if this is something easy or that I overlooked in the thread

---

### Post by bean123 on 2010-04-22
> **Zach Thomas said:**
> Hey bean, BURG is great! I'm really new to Ubuntu and not the smartest with computers, so maybe this is a silly question. But I intend to upgrade to 10.04 from 9.10 at the end of this month and was wondering how BURG will be affected? Do I need to change anything? Again sorry if this is something easy or that I overlooked in the thread

BURG PPA package is available for both jaunty, karmic and lucid, you just need a different source line in /etc/apt/source.list:

[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)

---

### Post by Starks on 2010-04-25
btw, your bbs url should be http, not https. secure connection is a 404.

---

### Post by bean123 on 2010-04-26
> **Starks said:**
> btw, your bbs url should be http, not https. secure connection is a 404.

Oh, thanks for the tip. I've fixed the link now.

---

### Post by krash1220 on 2010-04-26
Hey Bean,

You made a small error in the icons folder and small icons file. You have

-windows { image = "$$/small_win.png" }

and it should be

-windows { image = "$$/small_windows.png" }

I kept getting no icon beside my Windows entry and thought I had done something wrong.

---

### Post by tokyobadger on 2010-04-27
@bean123: many thanks for the informative answer and sorry for not saying it sooner - off to try out your suggestions ASAP :)

---

### Post by Xorlathor on 2010-04-27
That's pretty amazing! I think Canonical should come up with a default GRUB theme for lucid 10.10, then integrate it. Many people (including me) would be hesitant to mess with something as important as GRUB just for looks, it could end up trashing my whole system.

---

