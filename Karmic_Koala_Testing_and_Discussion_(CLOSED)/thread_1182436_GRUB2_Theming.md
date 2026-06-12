---
title: "GRUB2 Theming"
date: 2009-06-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2009-06-08
All right now---where's the theme change info???  :p:p:p

---

### Post by autocrosser on 2009-06-08
OK---simple hack......take a 640x480 png (I took all my xpm.gz images & converted them to .png so I would be safe about filesize) & rename it moreblue-orbit-grub.png. Drop it in your /boot/grub (saving the old moreblue somewhere else) & then do a sudo grub-mkconfig to update files......If you have selected a small enough file--moreblue is just under 50KB--you should have the image you wanted as your new grub2 screen---I don't know how to edit the grub.cfg file yet, so the magenta highlight will prevent some image colours---Have some fun!!!!!:D:D:D

---

### Post by geojorg on 2009-06-08
I just try this out and it work perfectly

[http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/](http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/)

---

### Post by ronacc on 2009-06-08
theres supposed to be a picture ? grub2 wrote a whole bunch of files with a .mod extension into my /boot/grub , but there is no moreblue-orbit.png, and now that I corrected the screwedup uuid and have it booting it looks exactly the same as the old grub except slower to gdm login .

---

### Post by autocrosser on 2009-06-08
Nice bit of info!!!  THANKS!!!!:popcorn:

For those who didn't goto the link:

_**Change the GRUB2 splash image**_

Now we will see how we can change the default GRUB2 splash image. First select the image file that you want to install from the following locations:
/usr/share/images/desktop-base/
/usr/share/images/grub/
For this example, I have selected &#8220;Plasma-lamp.tga&#8221; from /usr/share/images/grub/.
Now edit the file following file:
# nano /etc/grub.d/05_debian_theme
 and change the following line from:
 for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga}
**to**
for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/Plasma-lamp.{png,tga} and save the file.
 This basically tells GRUB2 to look for image name &#8220;Plasma-lamp&#8221; in the locations:
/boot/grub
/usr/share/images/desktop-base
/usr/share/images/grub
 Now you need to regenerate the grub.cfg file by giving the following command:
# update-grub
Updating /boot/grub/grub.cfg ...
Found Debian background: Plasma-lamp.tga
Found linux image: /boot/vmlinuz-2.6.26-rt1-rt
Found initrd image: /boot/initrd.img-2.6.26-rt1-rt
Found linux image: /boot/vmlinuz-2.6.26-1-686
Found initrd image: /boot/initrd.img-2.6.26-1-686
Found linux image: /boot/vmlinuz-2.6.25-2-686
Found initrd image: /boot/initrd.img-2.6.25-2-686
done
#

---

### Post by ronacc on 2009-06-08
it seems that there is more fouled up than I thought . I installed acording to the link in the first post this thread . I do  have the file /etc/grub.d/05_debian_theme and it reads as the part before the edit in autocrosser's post but there is no moreblue..... in /boot/grub or in /usr/share/images/desktop-base and there is no dir /usr/share/images/grub . it looks like something didn't get installed even though apt-get completed with no errors .

---

### Post by 23meg on 2009-06-08
Theming discussion moved to a separate thread.

---

### Post by autocrosser on 2009-06-09
> **ronacc said:**
> it seems that there is more fouled up than I thought . I installed acording to the link in the first post this thread . I do  have the file /etc/grub.d/05_debian_theme and it reads as the part before the edit in autocrosser's post but there is no moreblue..... in /boot/grub or in /usr/share/images/desktop-base and there is no dir /usr/share/images/grub . it looks like something didn't get installed even though apt-get completed with no errors .

You might try converting a old grub xpm to a png & use the info to point grub2 to it.....It is looking like something barfed in your install........

Luck to you my friend!!!!!

---

### Post by autocrosser on 2009-06-09
> **23meg said:**
> Theming discussion moved to a separate thread.

Thanks!!!!!

---

### Post by ronacc on 2009-06-09
I'll play with it some more tomorrow , 1 am  here and I don't trust myself to muck around too much with one eye closed and the other drooping :lolflag:

---

### Post by MacUntu on 2009-06-09
Now I'd just like the font to match the console font. Consistency ftw! :D

---

### Post by MacUntu on 2009-06-09
Almost there:

[[img]http://img.xrmb2.net/778275.jpg[/img]](http://img.xrmb2.net/images/778275.png)

Used PSF Tools ([http://www.seasip.info/Unix/PSF/](http://www.seasip.info/Unix/PSF/)) to convert the console font (/usr/share/consolefonts/Lat15-VGA16.psf in my case) to bdf. Then used grub-mkfont to generate a pf2 file from the bdf and copied it to /boot/grub/ascii.pf2 (did a backup of the original ascii.pf2 first - dirty hack).

Obviously there are some glyphs missing. ):P

**Edit:**
Seems PSF Tools screwed it up. I used the tool gbdfed to generate the bdf file (open, import, save as). Now it matches the console font (top: console font, bottom: original from GNU Unifont):

[[img]http://img.xrmb2.net/116715.jpg[/img]](http://img.xrmb2.net/images/116715.png)

---

### Post by NeoFax on 2009-06-10
Instead of using the old splashimages, has anyone tried to use gfxmenu?  Here is what I am talking about:

[http://bbs.archlinux.org/viewtopic.php?id=56576](http://bbs.archlinux.org/viewtopic.php?id=56576)
[http://grub.gibibit.com/About](http://grub.gibibit.com/About)
[http://forum.ubuntuusers.de/topic/grub2-gfxmenu-die-einfache-alternative-zu-gru/](http://forum.ubuntuusers.de/topic/grub2-gfxmenu-die-einfache-alternative-zu-gru/)

I would really like to use a deb file for this and not have to ./configure,make,make install.

---

### Post by autocrosser on 2009-06-10
That looks good---
I'll start playing with it this evening--about 4 hrs from now----I'll post what it's working like.....

---

### Post by andrewsomething on 2009-06-10
> **ronacc said:**
> it seems that there is more fouled up than I thought . I installed acording to the link in the first post this thread . I do  have the file /etc/grub.d/05_debian_theme and it reads as the part before the edit in autocrosser's post but there is no moreblue..... in /boot/grub or in /usr/share/images/desktop-base and there is no dir /usr/share/images/grub . it looks like something didn't get installed even though apt-get completed with no errors .

I haven' tested this yet, but I believe you need to have the desktop-base package installed for the current theme configuration to work properly. It's more or less Debian's version of the ubuntu-artwork package. The file: /usr/share/images/desktop-base/moreblue-orbit-grub.png is part of that package.

---

### Post by NCLI on 2009-06-10
I can't compile the graphical boot menu, seems like it will only compile on 32-bit systems :(

```
seph@NCLI-MAINFRAME:~/Desktop/gsoc08_r876$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for cmp... cmp
checking for bison... bison
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for ruby... no
checking for help2man... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether byte ordering is bigendian... no
checking for void *... yes
checking size of void *... 8
checking for long... yes
checking size of long... 8
checking for posix_memalign... yes
checking for memalign... yes
checking for asprintf... yes
checking for option to link raw image... -Wl,-N
checking for command to convert module to ELF format...
checking for objcopy... objcopy
checking for strip... strip
checking for nm... nm
checking whether optimization for size works... yes
checking whether -falign-loops works... yes
checking whether `gcc' generates calls to `__enable_execute_stack()'... no
checking whether `gcc' accepts `-fstack-protector'... yes
checking whether `gcc' accepts `-mstack-arg-probe'... no
checking whether target compiler is working... no
configure: error: cannot compile for the target
```

---

### Post by autocrosser on 2009-06-10
I have edited the grub.cfg file without having everything blow-up (or the world ending as the cfg would suggest ;) )---make sure you have saved the original file somewhere & work with a copy. It uses standard syntax, so look closely at it before making any changes--I was only doing copy/paste to avoid errors & now have my menu in a form I can like again :D.....I was having a problem in that OS-Prober scrambled my installed systems---I got rid of the--```
"root=/dev/sdc3"
``` old-style notation & used labels to force things the way I want them to go--with labels it should look like---```
"root=LABEL=KKbackup"
```....Go slow & make sure you REALLY know what you want---if it all barfs up--use a LiveCD & reinstall the stock grub.cfg & think about what went wrong......;)

---

### Post by Vanishing on 2009-06-10
seems like you can't change the resolution in grub.cfg if you want to use the tga files..
but maybe i'm wrong..:p

---

### Post by autocrosser on 2009-06-10
> **Vanishing said:**
> seems like you can't change the resolution in grub.cfg if you want to use the tga files..
but maybe i'm wrong..:p

I send an Email to the dev involved with the gfxmenu for grub2--waiting to hear back with info on what you can & can't do......

---

### Post by MacUntu on 2009-06-11
Had to reinstall GRUB2 to get the background working:

[[img]http://img.xrmb2.net/771492.jpg[/img]](http://img.xrmb2.net/images/771492.png)

And now I want a seamless transition to GDM. :P

Are there any known image property limits (like colors, size, ...)?

---

### Post by skylen on 2009-06-11
> **autocrosser said:**
> I send an Email to the dev involved with the gfxmenu for grub2--waiting to hear back with info on what you can & can't do......

Hi, I'm Colin D. Bennett, the author of the GRUB 2 graphical menu feature.

Glad to see that you are trying out the graphical menu.  I have been extremely busy since last summer so have not had a chance to work much on the graphical menu until the past few weeks.  I'm trying to iron out some wrinkles in it and prepare it for merging into GRUB's mainline.

To answer the question, there is nothing special about TGA images that prevents changing the screen resolution, but currently the graphical menu does not adapt properly when the screen size changes.  The reason is primarily that theme files specify layout in absolute pixel locations.

There are a few important items that I want to get implemented in the GRUB 2 graphical menu before I consider it totally ready for prime time:

[LIST]
[*]adapt menu screen to any video resolution
[*]fix memory leak when switching themes at runtime
[*]provide a pop-up menu to switch themes
[*]improve latency when navigating the menu by optimizing the repaint behavior
[/LIST]

I'll post updates to my web site at [http://grub.gibibit.com/]("http://grub.gibibit.com/") when there is something new, and hopefully in the near future it will be merged into GRUB mainline and begin appearing in official builds.

Regards,
Colin

---

### Post by autocrosser on 2009-06-11
Thanks for responding to my Email Colin!!!  Anything you can post that would give us more info would be very helpful---most of us here like being on the cutting edge & knowledge is the force that we need to blaze the trail that others will follow :D

Can you comment on the post in the last page that refers to the Arch forum?  I've downloaded what looks to be a very nice theme called grub2-theme-ubuntuglow. The Install file looks like this:```
post_install() {
cat << EOF

 Edit /boot/grub/grub.cfg , comment out your
     active set theme= line, and add this one:
     set theme="/boot/grub/themes/ubuntuglow/theme.txt"
     (Maybe without "/boot", depending on PC setup)

EOF
}

post_upgrade() {
        post_install
}

post_remove() {
cat << EOF

 IMPORTANT: Edit /boot/grub/grub.cfg , remove
     set theme="/boot/grub/themes/ubuntuglow/theme.txt"
     and uncomment an existing one / default!
     (Maybe without "/boot", depending on PC setup)

EOF
}
```

Question is: came this theme be used with the current version of Grub2 as we have installed? (I am including the file for you to look at....)

---

### Post by FrozenFox on 2009-06-12
Hello,

Same FrozenFox from the Arch thread you refer to..

Just fyi, ".install" files for Arch are a little misleading in name. The PKGBUILD file is where all the real work happens (if there is work to be done outside of copying files from the source tarball to the arch package; of course a theme pkgbuild file would contain no real 'work'). "Install" files are just for extra stuff that is handled pre/post install if necessary, whereas the PKGBUILD scripts copying/compiling/dependencies/package-information for the system. They handle giving the user information primarily (if such is absolutely necessary), but occasionally do things like make symbolic links or perform necessary actions to the system itself instead of on the package's files.

That said,

If I understand your post correctly **autocrosser**, you want to know if that file can work with the grub2 in the regular ubuntu repositories.. If so, the answer is highly likely to be "no", as I think Ubuntu uses normal grub2 which doesn't have Mr. Bennett's work added in yet afaict. However, I can't say with absolute certainty naturally, since I don't use Ubuntu anymore :p.

I apologize for the currently confusing name "grub2-theme-ubuntuglow". I would have named it grub2-gfxmenu-theme-ubuntuglow, but I knew that the project would be integrated into official grub2 eventually and didn't wish to change name conventions later on. Further, I really didn't expect such a vast amount of people to visit the little tutorial on Mr. Bennett's work (despite said work being awesome), particularly outside of the Arch community. 

It should theoretically be very straightforward to compile and install that stuff for Ubuntu though if you have moderate experience in doing so, at least for 32 bit users. Grub2 itself (with/without Mr. Bennett's work) cannot be compiled on 64 bit yet afaik; it needs to be done in 32 bit chroot or on a 32 bit install. It CAN be installed on 64 bit as a binary, just not compiled there. For that matter, you could probably model a .deb package out of the instructions and the existing pkgbuild+install file(s) pretty easily. If someone wants to though, note that I still need to fix the dependency list if you wish to reference that pkgbuild. With the help of a bunch of other people who tried it out on different setups who reported their results, I think most problems you might run into have solutions already added to the tutorial.

The only real difference in the tutorial instructions a non-Arch-user would need to know is instead of using makepkg to create an Arch package using the pkgbuilds, one would use the typical "./configure; make; sudo make install" (C-M-MI for short I suppose) and manually handle dependencies (such as ruby) and conflicts (ie removing grub or normal grub2 with apt). If there are any special instructions needed, the PKGBUILD in the tarballs I made gives an idea of what you would need to do. The overlay pkgbuild, for instance, does nothing more than extract Mr. Bennett's tarball and re-compress it as pkg.tar.gz in the arch package directory (pkgdir) + information. It could be re-done as a single "cp -r" line install of all the recursive "install" lines, but we try to keep from doing that if it's not too complicated for various reasons, primarily having to do with permissions. For exampel, the only thing necessary there for non-Archers would be to copy the overlay files from Mr. Bennett's tarball to the respective places in your system, which is what would effectively happen with that pkgbuild+makepkg+installing it would do.

Also fyi, as-is, the themes need to be tweaked for different resolutions, but they do work fine. I use 1024x768, the default is 640x480 i think, and several others have used an odd eeepc resolution after including a 915resolution.mod file and a couple tweaks to grub.cfg in addition to the theme. Looking forward to more happily scalable theme capabilities to deal with this issue :).

---

### Post by pelle.k on 2009-06-12
I dont know to what extent grub2 is supposed to be able to theme, but i really (really, really, really) hope there will be some way to remove
[LIST]
[*]borders
[*]Version info text at the top
[*]Help text at the bottom
[/LIST]
It looks really messy as it is now (grub legacy), and i don't really need any fancy graphics, or animations (although that could be nice) - just the ability to have grub not point me in the eyes so much by default. :)
Look at an white/black standard grub (don't even get me started at the white/black/blue one... hehe), and a mockup i made. Simplicity is much more pleasing to the eyes, me thinks (the second, and third one). With a splashimage, it looks even better, where the borders on the "standard grub" would spoil it a bit.

PS. skylen, thanks for all the hard work you're doing, along with the rest of the open source community, of course :)

---

### Post by autocrosser on 2009-06-12
Thanks for the heads-up FrozenFox--I'll look into reworking it for Ubnutu this weekend--will post with results.....


> **FrozenFox said:**
> Hello,

Same FrozenFox from the Arch thread you refer to..

Just fyi, ".install" files for Arch are a little misleading in name. The PKGBUILD file is where all the real work happens (if there is work to be done outside of copying files from the source tarball to the arch package; of course a theme pkgbuild file would contain no real 'work'). "Install" files are just for extra stuff that is handled pre/post install if necessary, whereas the PKGBUILD scripts copying/compiling/dependencies/package-information for the system. They handle giving the user information primarily (if such is absolutely necessary), but occasionally do things like make symbolic links or perform necessary actions to the system itself instead of on the package's files.

That said,

If I understand your post correctly **autocrosser**, you want to know if that file can work with the grub2 in the regular ubuntu repositories.. If so, the answer is highly likely to be "no", as I think Ubuntu uses normal grub2 which doesn't have Mr. Bennett's work added in yet afaict. However, I can't say with absolute certainty naturally, since I don't use Ubuntu anymore :p.

I apologize for the currently confusing name "grub2-theme-ubuntuglow". I would have named it grub2-gfxmenu-theme-ubuntuglow, but I knew that the project would be integrated into official grub2 eventually and didn't wish to change name conventions later on. Further, I really didn't expect such a vast amount of people to visit the little tutorial on Mr. Bennett's work (despite said work being awesome), particularly outside of the Arch community. 

It should theoretically be very straightforward to compile and install that stuff for Ubuntu though if you have moderate experience in doing so, at least for 32 bit users. Grub2 itself (with/without Mr. Bennett's work) cannot be compiled on 64 bit yet afaik; it needs to be done in 32 bit chroot or on a 32 bit install. It CAN be installed on 64 bit as a binary, just not compiled there. For that matter, you could probably model a .deb package out of the instructions and the existing pkgbuild+install file(s) pretty easily. If someone wants to though, note that I still need to fix the dependency list if you wish to reference that pkgbuild. With the help of a bunch of other people who tried it out on different setups who reported their results, I think most problems you might run into have solutions already added to the tutorial.

The only real difference in the tutorial instructions a non-Arch-user would need to know is instead of using makepkg to create an Arch package using the pkgbuilds, one would use the typical "./configure; make; sudo make install" (C-M-MI for short I suppose) and manually handle dependencies (such as ruby) and conflicts (ie removing grub or normal grub2 with apt). If there are any special instructions needed, the PKGBUILD in the tarballs I made gives an idea of what you would need to do. The overlay pkgbuild, for instance, does nothing more than extract Mr. Bennett's tarball and re-compress it as pkg.tar.gz in the arch package directory (pkgdir) + information. It could be re-done as a single "cp -r" line install of all the recursive "install" lines, but we try to keep from doing that if it's not too complicated for various reasons, primarily having to do with permissions. For exampel, the only thing necessary there for non-Archers would be to copy the overlay files from Mr. Bennett's tarball to the respective places in your system, which is what would effectively happen with that pkgbuild+makepkg+installing it would do.

Also fyi, as-is, the themes need to be tweaked for different resolutions, but they do work fine. I use 1024x768, the default is 640x480 i think, and several others have used an odd eeepc resolution after including a 915resolution.mod file and a couple tweaks to grub.cfg in addition to the theme. Looking forward to more happily scalable theme capabilities to deal with this issue :).

---

### Post by shakaran on 2009-06-12
Hi, anyone with experience (or the author) can make a .deb? It would be useful.

Thanks.

---

### Post by skylen on 2009-06-12
> **FrozenFox said:**
> If I understand your post correctly **autocrosser**, you want to know if that file can work with the grub2 in the regular ubuntu repositories.. If so, the answer is highly likely to be "no", as I think Ubuntu uses normal grub2 which doesn't have Mr. Bennett's work added in yet afaict.
You are right; I'm pretty sure that Ubuntu is not integrating my gfxmenu patch yet, especially since I haven't published the updates for many months... though I plan to in the next days and weeks.

> **FrozenFox said:**
> It should theoretically be very straightforward to compile and install that stuff for Ubuntu though if you have moderate experience in doing so, at least for 32 bit users. Grub2 itself (with/without Mr. Bennett's work) cannot be compiled on 64 bit yet afaik; it needs to be done in 32 bit chroot or on a 32 bit install. It CAN be installed on 64 bit as a binary, just not compiled there.
I don't know about the GRUB 2 source snapshot you're using, but GRUB SVN trunk builds on 64-bit Ubuntu now for me.  It did have problems at some point a couple weeks or months ago, however, but that has been fixed.

Cheers,
Colin

---

### Post by skylen on 2009-06-12
> **pelle.k said:**
> I dont know to what extent grub2 is supposed to be able to theme, but i really (really, really, really) hope there will be some way to remove
[LIST]
[*]borders
[*]Version info text at the top
[*]Help text at the bottom
[/LIST]
It looks really messy as it is now (grub legacy), and i don't really need any fancy graphics, or animations (although that could be nice) - just the ability to have grub not point me in the eyes so much by default. :)
Look at an white/black standard grub (don't even get me started at the white/black/blue one... hehe), and a mockup i made. Simplicity is much more pleasing to the eyes, me thinks (the second, and third one). With a splashimage, it looks even better, where the borders on the "standard grub" would spoil it a bit.

That is a great idea.  I like your cleaned-up version of the GRUB text menu.  I should post to the developers' list and see if anyone wants to step up and do it.

---

### Post by autocrosser on 2009-06-12
I think that a editor similar to what is available for grub should be encouraged...I have been doing manual editing for now, but that is a less than optimal option ;) & can really result in a b0rked system........The developer for SUM should be brought into the loop very soon. I'll contact him over the weekend to see if he is interested....

I just contacted the dev for SUM---will see if he will come in & add to the discussion......

---

### Post by autocrosser on 2009-06-12
> **skylen said:**
> You are right; I'm pretty sure that Ubuntu is not integrating my gfxmenu patch yet, especially since I haven't published the updates for many months... though I plan to in the next days and weeks.


I don't know about the GRUB 2 source snapshot you're using, but GRUB SVN trunk builds on 64-bit Ubuntu now for me.  It did have problems at some point a couple weeks or months ago, however, but that has been fixed.

Cheers,
Colin


Colin--can you check Ubuntu32 for build?  If it will, I'm more than game to get it running on my system for testing & I'm sure that several of the others here are ready to step up also....

I'm setup for building just about anything here ;)

---

### Post by pferraro on 2009-06-12
> **autocrosser said:**
> 
Now edit the file following file:
# nano /etc/grub.d/05_debian_theme
 and change the following line from:
 for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga}
**to**
for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/Plasma-lamp.{png,tga} and save the file.


I would recommend against this.  Any future updates to the grub-pc package (inevitable this early in the dev cycle) will wipe out your changes to /etc/grub.d/05_debian_theme.  Instead, it would be much simpler to create a sym link to the expected file location.
e.g.
ln -s /usr/share/images/grub/Plasma-lamp.tga /boot/grub/moreblue-orbit-grub.tga

---

### Post by Starks on 2009-06-12
What happens to startup-manager now?

---

### Post by olskar on 2009-06-12
> **Starks said:**
> What happens to startup-manager now?



> StartUp Manager, or SUM, is a gui tool for changing settings for Grub, **Grub2**, Usplash and Splashy.
SUM should work with recent versions of Debian and Debian-based distributions such as Ubuntu.

Should work fine :)

---

### Post by Starks on 2009-06-12
> **NeoFax said:**
> Instead of using the old splashimages, has anyone tried to use gfxmenu?  Here is what I am talking about:

[http://bbs.archlinux.org/viewtopic.php?id=56576](http://bbs.archlinux.org/viewtopic.php?id=56576)
[http://grub.gibibit.com/About](http://grub.gibibit.com/About)
[http://forum.ubuntuusers.de/topic/grub2-gfxmenu-die-einfache-alternative-zu-gru/](http://forum.ubuntuusers.de/topic/grub2-gfxmenu-die-einfache-alternative-zu-gru/)

I would really like to use a deb file for this and not have to ./configure,make,make install.
You didn't look hard enough. There are Debian-intended debs floating around.

---

### Post by autocrosser on 2009-06-12
> **olskar said:**
> Should work fine :)

There are a couple of bug reports already about SUM not working with grub2--be advised to not use SUM to try to mod the grub.cfg until things are sorted out..I have invited the SUM dev to add input here--we'll see if he comes.......

---

### Post by autocrosser on 2009-06-12
> **pferraro said:**
> I would recommend against this.  Any future updates to the grub-pc package (inevitable this early in the dev cycle) will wipe out your changes to /etc/grub.d/05_debian_theme.  Instead, it would be much simpler to create a sym link to the expected file location.
e.g.
ln -s /usr/share/images/grub/Plasma-lamp.tga /boot/grub/moreblue-orbit-grub.tga


I am "expecting" that is the way SUM (when it's reworked) will do things--I just posted that snip in its total from the Arch link....I am sure that there will be several "ways" to do things in the near term--that is just the second way I've tried it.....

---

### Post by FrozenFox on 2009-06-12
Regarding Grub2 compiling on 64 bit natively as of recent-ish releases:

Thanks for letting me know. I'll update the pkgbuild and such upon your next self-contained source release accordingly :) . I'm sure people uncomfortable with using the built packages I put up for those without a 32 compile area will be very happy to know this. Good for me too, since I can skip building them altogether to post if I wanted to.

---

### Post by Starks on 2009-06-12
Stupid question...

Are gfxboot and gfxmenu the same thing?

---

### Post by autocrosser on 2009-06-12
Similar thoughts--different rendering.....Different developers...

---

### Post by NeoFax on 2009-06-13
> **Starks said:**
> You didn't look hard enough. There are Debian-intended debs floating around.

If so, would you please point me in the right direction?  I am pretty sure these are the old grub-gfxmenu/gfxboot debs.

---

### Post by Starks on 2009-06-13
> **NeoFax said:**
> If so, would you please point me in the right direction?  I am pretty sure these are the old grub-gfxmenu/gfxboot debs.
Nope. Quite new.

[http://sidux.com/debian/pool/main/g/grub-gfxboot/](http://sidux.com/debian/pool/main/g/grub-gfxboot/)

Make sure to remove grub and startupmanager before dpkg'ing the deb.

---

### Post by FrozenFox on 2009-06-13
> **Starks said:**
> 
[QUOTE=NeoFax]Instead of using the old splashimages, has anyone tried to use gfxmenu? Here is what I am talking about:

[http://bbs.archlinux.org/viewtopic.php?id=56576](http://bbs.archlinux.org/viewtopic.php?id=56576)
[http://grub.gibibit.com/About](http://grub.gibibit.com/About)
[http://forum.ubuntuusers.de/topic/gr...native-zu-gru/](http://forum.ubuntuusers.de/topic/gr...native-zu-gru/)

I would really like to use a deb file for this and not have to ./configure,make,make install.

You didn't look hard enough. There are Debian-intended debs floating around.

[QUOTE=NeoFax] If so, would you please point me in the right direction? I am pretty sure these are the old grub-gfxmenu/gfxboot debs.[/QUOTE]

Nope. Quite new.

[http://sidux.com/debian/pool/main/g/grub-gfxboot/](http://sidux.com/debian/pool/main/g/grub-gfxboot/)

Make sure to remove grub and startupmanager before dpkg'ing the deb.[/QUOTE]

I don't know what's with the condescending tone / general asshattery about "not looking hard enough" in your prior post (I really tried to see it as anything other than a rude comment via misinterpretation from being text btw, but those wholly unnecessary specific words made that impossible), but what NeoFax linked to and what you linked to are not anywhere near the same thing, despite unfortunately somewhat similar names. Your debs link to grub **legacy** with simple gfxboot patches (0.9x series, which is **going away completely** as a default in the next ubuntu), whereas the project NeoFax is interested in is grub2 with Mr. Bennett's work for adding advanced graphical theming patched in (ie "1.96", a ***total re-write*** of what you linked to regarding *both* the grub bootloader code *and* code for graphical capabilities; **grub2-gfxmenu is FAR more advanced in nearly every respect**). Maybe you're the one who didn't look hard enough. Further, despite the deb you linked to being fairly new, grub-gfxboot/gfxmenu (ie legacy grub + patches) themselves are not new by any stretch of the imagination, and debs for it have been around for a *very* long time.

If you looked at the linked pages before commenting, you would have seen..

1) Grub"2" (ie 1.96) versus grub "0.97"
2) The arch forum thread linked to first *specifically* mentions (in the introduction..) ubuntu not having said stuff, ubuntu packages, and the fact that a couple of the themes were modelled after those ancient grub-gfxboot themes **and** specifies that they are not the same projects *by name*.
3) Furthermore, NeoFax even referred to knowing about grub-gfxboot/menu debs.. didn't that even make you pause for a second?

---

### Post by pelle.k on 2009-06-13
Chill man. Although you are correct, i can see how he made the assumption that you were referring to the "new" old gfxboot, wich has made it in to sidux by now, where the "old" old gfxboot themes doesn't seem to work anymore.
Mistakes are easy to make. ;)

EDIT: good writeup at the arch forums, althoug now my heads hurts a little bit, hehe :)

---

### Post by FrozenFox on 2009-06-13
Fyi I'm not the one who Starks was responding to. The convo in question was between Starks and NeoFax, not myself; his comment just warranted a response.

I would fully agree with you that the mistake and comment would be completely understandable had it not been for adding in "you didn't look hard enough" to NeoFax when Starks himself was the one who didn't bother to look, particularly when NeoFax both gave links *and* acknowledged the existence of the debs he was about to link to in the next post.. Even after reflecting for a moment, my response was fully justified, IMO. People don't need to assume someone else didn't do their homework when the proof is right in front of them that they did. He *linked* to it. Had NeoFax not specifically provided links, I would not have found Starks' response irritating at all and my response would have been a simple correction.

However, that's not the case.

---

### Post by Jimmy_r on 2009-06-15
> **autocrosser said:**
> There are a couple of bug reports already about SUM not working with grub2--be advised to not use SUM to try to mod the grub.cfg until things are sorted out..I have invited the SUM dev to add input here--we'll see if he comes.......

Hi, here I am :)

I have not been following this stuff so much lately, been waiting for things to get ironed out and decided upon.

My current plan is to make a startupmanager 2 that will work with grub2 only(trying to autodetect the version of grub was too hacky).

Now, the questions I will try to find an answer to before doing this are:

What will be the best way to configure grub2 programatically?

Editing grub.cfg directly or will that get overwritten by update-grub(grub-mkconfig)?

In case it is overwritten, how to configure it through /etc/grub.d/* ?
Since the files in there are scripts, it would be too difficult to try to parse and edit them directly so the only solution I can see would be to have a specific XX_startupmanager file in /etc/grub.d that would be reliable to parse.

And lastly, will all this stuff work the same in (at least)Debian as in Ubuntu so there wont be a similar situation as now where update-grub works differently between them[1].

[1] [https://answers.launchpad.net/startup-manager/+faq/497](https://answers.launchpad.net/startup-manager/+faq/497)

---

### Post by dino99 on 2009-06-15
hi,
parallel question:
is anyone had this error: "alloc magic is broken" ?
can't find a workaround
Sorry to post here, it's with jaunty repo, so do you think i can try grub-pc & os-prober from karmic repo with jaunty ?

(have no problem with karmic)

---

### Post by Starks on 2009-06-15
Jimmy, will you have a version control repo that we can follow your progress with?

I'm quite interested.

---

### Post by autocrosser on 2009-06-15
> **Jimmy_r said:**
> Hi, here I am :)

I have not been following this stuff so much lately, been waiting for things to get ironed out and decided upon.

My current plan is to make a startupmanager 2 that will work with grub2 only(trying to autodetect the version of grub was too hacky).

Now, the questions I will try to find an answer to before doing this are:

What will be the best way to configure grub2 programatically?

Editing grub.cfg directly or will that get overwritten by update-grub(grub-mkconfig)?

In case it is overwritten, how to configure it through /etc/grub.d/* ?
Since the files in there are scripts, it would be too difficult to try to parse and edit them directly so the only solution I can see would be to have a specific XX_startupmanager file in /etc/grub.d that would be reliable to parse.

And lastly, will all this stuff work the same in (at least)Debian as in Ubuntu so there wont be a similar situation as now where update-grub works differently between them[1].

[1] [https://answers.launchpad.net/startup-manager/+faq/497](https://answers.launchpad.net/startup-manager/+faq/497)


GREAT to see you here!!!  Welcome & looking forwards to interesting information!!!!

---

### Post by Jimmy_r on 2009-06-16
> **Starks said:**
> Jimmy, will you have a version control repo that we can follow your progress with?

I'm quite interested.

I will use [https://code.launchpad.net/~jimmy-ronnholm/startup-manager/](https://code.launchpad.net/~jimmy-ronnholm/startup-manager/) for code. When I start working on it, I dont think it will take long until I start releasing debs either.

---

### Post by autocrosser on 2009-06-16
THANKS Jimmy!!!!!  Looking forward to it!!

As soon as you have some debs---post them here--I'm more than happy to test.....

---

### Post by hugmenot on 2009-06-18
Hi, I entered gfxmode=1440x900, i.e., the native resolution of my LCD. I only get a scrambled screen. Is there anything I am missing?

---

### Post by xtoudi on 2009-06-18
> **hugmenot said:**
> Hi, I entered gfxmode=1440x900, i.e., the native resolution of my LCD. I only get a scrambled screen. Is there anything I am missing?

Be sure you are using a background image of the same size you've chosen in set gfxmode= line.
You can even set:

gfxmode=1440x900x32

if your video card framebuffer can support it and should be compiled in I guess.

---

### Post by hugmenot on 2009-06-18
> **xtoudi said:**
> if your video card framebuffer can support it and should be compiled in I guess.

I use KMS and the display switches to 1440x900 directly after grub. Does this mean it should work with grub2 as well? And what do you mean with »should be compiled in«?

---

### Post by xtoudi on 2009-06-18
> **hugmenot said:**
> I use KMS and the display switches to 1440x900 directly after grub. Does this mean it should work with grub2 as well? And what do you mean with »should be compiled in«?

I really don't know what I mean ... to much beer :-)
Forget about KMS - KMS starts as you said after GRUB2 and it is kernel-mode-settings.
Check your background image resolution - only this I can figure out at this time - maybe tomorrow it'll be better time :-)

---

### Post by ranch hand on 2009-06-18
Your background image needs to be the same as the background images that work.  Compare them.

When I edit photos for background on my 1400x600 I resize them to 750x300 and then they fit with the resolution they have.

If you havean image that fits, pull it up in Gimp and see what it is  and then make the one you want the same.  You want to look under "image->properties in gimp.

---

### Post by UbuWu on 2009-07-13
> **pelle.k said:**
> I dont know to what extent grub2 is supposed to be able to theme, but i really (really, really, really) hope there will be some way to remove
[LIST]
[*]borders
[*]Version info text at the top
[*]Help text at the bottom
[/LIST]
It looks really messy as it is now (grub legacy), and i don't really need any fancy graphics, or animations (although that could be nice) - just the ability to have grub not point me in the eyes so much by default. :)
Look at an white/black standard grub (don't even get me started at the white/black/blue one... hehe), and a mockup i made. Simplicity is much more pleasing to the eyes, me thinks (the second, and third one). With a splashimage, it looks even better, where the borders on the "standard grub" would spoil it a bit.

PS. skylen, thanks for all the hard work you're doing, along with the rest of the open source community, of course :)

Posted this on brainstorm here: [http://brainstorm.ubuntu.com/idea/20406/](http://brainstorm.ubuntu.com/idea/20406/)

---

### Post by klim8 on 2009-07-13
Check this:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/392680](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/392680)

---

### Post by MacUntu on 2009-07-13
It's possible that your video card just doesn't support that resolution without a driver.

**Edit:**
You can press 'c' at the GRUB2 menu to get a command line. Enter the command 'vbeinfo' and it will list all available resolutions. If the desired resolution isn't there, it's not a bug and limited by your hardware (if you have the T400 with a dedicated Radeon GPU you can try if it supports that resolution).

---

### Post by autocrosser on 2009-08-08
Have not done much here in the last couple of weeks--so I modified the GDM Jaunty image to work with Grub2...just drop it into your /usr/share/images/grub & then edit /etc/grub.d/05_debian_theme  by doing a
```
gksudo gedit /etc/grub.d/05_debian_theme
```I changed the lines to look like:
```
# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/grub}/ubuntu.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found Debian background: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=red/black
  set color_highlight=magenta/black
else
EOF
fi
```And then be sure to do
```
sudo update-grub2
```Enjoy!!!

It looks like the second shot....

---

### Post by Starks on 2009-08-09
How should I edit my grub.cfg after installing grub2-gfxmenu from scratch?

---

### Post by autocrosser on 2009-08-09
not sure--I've sent a email to Colin about the current state of the menu..waiting to hear back from him........

---

### Post by Starks on 2009-08-09
> **autocrosser said:**
> not sure--I've sent a email to Colin about the current state of the menu..waiting to hear back from him........
I've managed to get certain things to display, but not a whole theme. The directions I've come across are too Arch-centric.

I really don't like playing around with grub.cfg blindly. <___<

---

### Post by autocrosser on 2009-08-09
Hang in there--As soon as Colin gets back to me with info---I'll post it...

---

### Post by ranch hand on 2009-08-09
> **Starks said:**
> I've managed to get certain things to display, but not a whole theme. The directions I've come across are too Arch-centric.

I really don't like playing around with grub.cfg blindly. <___<
Leave grub.cfg alone.  If you have set the debian_theme file correctly and run update-grub the grub.cfg file will take be generated correctly.

The grub.cfg file is wuto generated each time you run update-grub so manually editing it is kind of silly but easy to fix by running update-grub.

My debian_theme file (just the changed parts) looks like this;
```

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base}/NICE.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)		reader=png ;;
        *.tga)		reader=tga ;;
        *.jpg|*.jpeg)	reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found Debian background: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
## set color_normal=black/black
  set color_normal=green/black
  set color_highlight=yellow/black
else
EOF
fi

```
I just changed the image I wanted to use from .jpg to .png and put it in the right directories.

I had to change the colors so that I could read the menu on top of the image - green and yellow work for my image but I may change the green to white.

After ANY change to ANY file related to grub2 you MUST run update-grub.

It works pretty slick.  When you have 10 OS' it does take time but it is faster than hand editing grub-legacy.  I am falling in love.

---

### Post by wayne_cat on 2009-08-09
> **autocrosser said:**
> Hang in there--As soon as Colin gets back to me with info---I'll post it...

thanks for the efforts.

---

### Post by Nate B. on 2009-08-09
I have grub-pc 1.96+20090725-1ubuntu1 installed and it's working fine except that I can't get a splash image on the screen.  None of the images from the grub2-splashimages package works nor does the image I used in grub-legacy which I converted to .png.

Here is the relevant portion of /boot/grub.cfg:
```
### BEGIN /etc/grub.d/05_nates_theme ###
set root=(hd0,3)
search --no-floppy --fs-uuid --set 8dd94a6d-0613-4c3a-ad4d-701b03a0a662
insmod png
if background_image /boot/grub/linuxinside.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_nates_theme ###

```

(I copied the debian theme file to a local copy and edited the path and file name in it.)

However, all I see is the text grub screen as specified by the 'else' branch.

:confused:

Is this a known bug in grub-pc later than the version on the Alpha 3 CD?

---

### Post by autocrosser on 2009-08-09
No--I just reinstalled late last week & my grub2 works as expected....are you doing a  
```
gksudo gedit /etc/grub.d/05_debian_theme 
```to edit the image part of your grub.cfg?

I see it--you can't do "05_nates_theme" grub2 is very literal about what is where...it REALLY needs to be 05_debian_theme & then edit the image & colour lines only.

My grub.cfg looks like:```
### BEGIN /etc/grub.d/05_debian_theme ###
set root=(hd2,2)
search --no-floppy --fs-uuid --set fc1446a5-94e9-40f8-9ebb-2442107fc13c
insmod png
if background_image /usr/share/images/grub/ubuntu.png ; then
  set color_normal=red/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###
```

---

### Post by ranch hand on 2009-08-09
> **Nate B. said:**
> I have grub-pc 1.96+20090725-1ubuntu1 installed and it's working fine except that I can't get a splash image on the screen.  None of the images from the grub2-splashimages package works nor does the image I used in grub-legacy which I converted to .png.

Here is the relevant portion of /boot/grub.cfg:
```
### BEGIN /etc/grub.d/05_nates_theme ###
set root=(hd0,3)
search --no-floppy --fs-uuid --set 8dd94a6d-0613-4c3a-ad4d-701b03a0a662
insmod png
if background_image /boot/grub/linuxinside.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_nates_theme ###

```

(I copied the debian theme file to a local copy and edited the path and file name in it.)

However, all I see is the text grub screen as specified by the 'else' branch.

:confused:

Is this a known bug in grub-pc later than the version on the Alpha 3 CD?
I have been having trouble with the bug with 

sorry this screwed up somehow.  I will repost later.  You are in the wrong spot on the page you need to move up the page and change the name of the file there.

I have to go or I would copy my file - Later.

---

### Post by Starks on 2009-08-10
ranch hand, I was talking about gfxmenu, not changing my GRUB2 image.

---

### Post by autocrosser on 2009-08-10
He was "chiming" in---I do believe that he 'aught to read things a wee bit closer though.....

---

### Post by phenest on 2009-08-10
> **autocrosser said:**
> I see it--you can't do "05_nates_theme" grub2 is very literal about what is where...it REALLY needs to be 05_debian_theme & then edit the image & colour lines only.

Yep. I tried writing my own theme script, to no avail. I just edited the 05_debian_theme instead, which works fine.

---

### Post by tekstr1der on 2009-08-10
Be sure to back up those custom 05_debian_theme and /etc/default/grub files today folks! Latest grub2 update replaces the files with new defaults.

---

### Post by ranch hand on 2009-08-10
> **autocrosser said:**
> He was "chiming" in---I do believe that he 'aught to read things a wee bit closer though.....
Not only that, the bugger shouldn't do it too late at night when he is more simple than normal.

Sorry.

---

### Post by Nate B. on 2009-08-10
> **autocrosser said:**
> No--I just reinstalled late last week & my grub2 works as expected....are you doing a  
```
gksudo gedit /etc/grub.d/05_debian_theme 
```to edit the image part of your grub.cfg?

No, I do `sudo mc' as this is on Kubuntu and gedit isn't installed.  I prefer the built-in Midnight Commander editor.

> I see it--you can't do "05_nates_theme" grub2 is very literal about what is where...it REALLY needs to be 05_debian_theme & then edit the image & colour lines only.

I didn't think the *name* of the file mattered so long as what gets put into grub.cfg was correct.  In fact, I started out by modifying the 05_debian_theme file and it didn't work from there either.

Comparing our relevant lines, I see no difference other than UUID, image path/filename, and color choices.  The source script file name is hidden from grub2 by triple hashes and is included for our (human) benefit.

Perhaps it's a permissions issue, although I don't see how since I doubt the first stage of grub2 understands such minutia.

---

### Post by dinxter on 2009-08-10
i managed to manhandle the [patch here]("http://grub.gibibit.com/Download") into the package source and added the themes and so on, looks nice! i was wondering if anyone else has slow menu redrawing though? i had to drop a few grub_vbe_bios_set_display_start lines in videotest, i didn't have the talent to sort it out properly, so i was curious if its a gfxmenu problem or my cackhanded packaging :)

---

### Post by phenest on 2009-08-10
What about the other stuff in 05_debian_theme that doesn't get put into grub.cfg? grub.cfg isn't the only thing grub2 uses when it loads. Stuff has to be 'set' first when update-grub in called. Try looking at the difference between your05_nates_theme and 05_debian_theme.

---

### Post by dinxter on 2009-08-10
just in case anyone using gfxmenu wants it, attached is the script i'm using for /etc/grub.d/ to set it up. with the themes/fonts/images from the gfxmenu website, overlay_2009-07-19, in /boot/grub.

---

### Post by autocrosser on 2009-08-10
Thanks Dinxter!!!  I'll be looking into that this evening!!!

---

### Post by autocrosser on 2009-08-10
> **Nate B. said:**
> No, I do `sudo mc' as this is on Kubuntu and gedit isn't installed.  I prefer the built-in Midnight Commander editor.



I didn't think the *name* of the file mattered so long as what gets put into grub.cfg was correct.  In fact, I started out by modifying the 05_debian_theme file and it didn't work from there either.

Comparing our relevant lines, I see no difference other than UUID, image path/filename, and color choices.  The source script file name is hidden from grub2 by triple hashes and is included for our (human) benefit.

Perhaps it's a permissions issue, although I don't see how since I doubt the first stage of grub2 understands such minutia.


It's my understanding that if grub2 does not "see" a part of it's config it will supply known defaults...I think that is where you are.......you might try re-editing the deb & do a sudo update grub2 to see if it comes round.....

I'm not close to my system right now (at slave-job), but I'll post my deb file in about 4 hours for you to look at...maybe you should reinstall all your grub2 stuff--I know a update will be in today, so that might be a good time to re-do it....

---

### Post by autocrosser on 2009-08-10
> **tekstr1der said:**
> Be sure to back up those custom 05_debian_theme and /etc/default/grub files today folks! Latest grub2 update replaces the files with new defaults.


VERY good point!!!! I'll be doing that very thing as soon as I get back home & then see where the "new" grub2 update takes me--has anyone looked at what is included?  I have heard that the GFX menu stuff is close---What say you Dinxter???? :)

---

### Post by dinxter on 2009-08-10
attached is the gfxmenu patch on grub-pc 1.96+20090725-1ubuntu2, if someone wants to uncomment the handful of // lines and fix the problems. something to do with including the startup.S functions, beyond me :) i'll stick it in a ppa anyway since i'm using the hacked package ok

---

### Post by dinxter on 2009-08-10
the new grub looks quite small, some hidden timeout stuff and debian_theme plus a gfxpayload patch. 
would be nice if gfxmenu arrived in time, i notice that xsplash has just arrived too, boot could look spectacular, if it isnt so quick that you miss it all :)

---

### Post by wayne_cat on 2009-08-10
Which // line do you mean ... have just found to functions to test VBE .. what happens if "vbeerr != 0"  ... does not look harmful

---

### Post by dinxter on 2009-08-10
> **wayne_cat said:**
> Which // line do you mean ... have just found to functions to test VBE .. what happens if "vbeerr != 0"  ... does not look harmful

theres a couple of bits in commands/videotest.c and  video/i386/pc/vbe.c like 
vbestatus = grub_vbe_bios_set_display_start (0, i);
i had to comment out to build on amd64. grub_vbe_bios_set_display_start  is assembly defined in kern/ for different arch . but debuild isnt finding it so it fails on implicit decleration

both bzr and patched versions build fine so i think its something that has to go into the packaging stuff in debian/ . but grub packaging is more complex that i can follow properly. if you know what to stick where to get it to package properly with grub_vbe_bios_set_display_start included that would be cool. i dont think its critical, its for testing, but it annoys my sense of completeness to comment it out!

---

### Post by wayne_cat on 2009-08-10
> **dinxter said:**
> theres a couple of bits in commands/videotest.c and  video/i386/pc/vbe.c like 
vbestatus = grub_vbe_bios_set_display_start (0, i);
i had to comment out to build on amd64. grub_vbe_bios_set_display_start  is assembly defined in kern/ for different arch . but debuild isnt finding it so it fails on implicit decleration

both bzr and patched versions build fine so i think its something that has to go into the packaging stuff in debian/ . but grub packaging is more complex that i can follow properly. if you know what to stick where to get it to package properly with grub_vbe_bios_set_display_start included that would be cool. i dont think its critical, its for testing, but it annoys my sense of completeness to comment it out!

ahh ... ok .. just searched in the patch ... I will have a look at it ... maybe I can find the problem

---

### Post by Starks on 2009-08-10
> **dinxter said:**
> just in case anyone using gfxmenu wants it, attached is the script i'm using for /etc/grub.d/ to set it up. with the themes/fonts/images from the gfxmenu website, overlay_2009-07-19, in /boot/grub.
What do I do after running it? The output is a bit confusing.

---

### Post by autocrosser on 2009-08-10
Two things---the update was handled very gracefully & asked if I wanted to keep my deb file---I of course, said Yes....

Secondly--this was reported elsewhere, but I feel that it should be included here also....

From Colin Watson:> As of today's GRUB 2 upload to Karmic, the boot menu is hidden by 
default, which was the way it was by default with GRUB Legacy. For those 
of you with other operating systems installed, this is not the correct 
default, but it was difficult to see how to preserve this automatically 
in a reasonable way. 
 
If you're upset by the boot menu being hidden all of a sudden, then you 
should edit /etc/default/grub, comment out the GRUB_HIDDEN_TIMEOUT line, 
and set GRUB_TIMEOUT to the timeout you want in seconds (say "10"), then 
run 'sudo update-grub'. 
 
Although I'm not *too* worried about upgrades through Karmic being a 
little rocky in the cause of getting to the right place in the end (so 
I'm just posting instructions here on the basis that most people running 
Karmic ought to be following -devel-announce), we do of course still 
need to clear up the upgrade for upgraders from 9.04. This is filed as 
[https://bugs.launchpad.net/ubuntu/+s...b2/+bug/386789]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/386789"). 
 
Thanks, 
 
-- 
Colin Watson                                       [cjwatson@ubuntu.com] 
 
-- 
ubuntu-devel-announce mailing list 
[EMAIL="ubuntu-devel-announce@lists.ubuntu.com"]ubuntu-devel-announce@lists.ubuntu.com[/EMAIL] 
[https://lists.ubuntu.com/mailman/lis...devel-announce]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce")

---

### Post by autocrosser on 2009-08-10
> **Nate B. said:**
> No, I do `sudo mc' as this is on Kubuntu and gedit isn't installed.  I prefer the built-in Midnight Commander editor.



I didn't think the *name* of the file mattered so long as what gets put into grub.cfg was correct.  In fact, I started out by modifying the 05_debian_theme file and it didn't work from there either.

Comparing our relevant lines, I see no difference other than UUID, image path/filename, and color choices.  The source script file name is hidden from grub2 by triple hashes and is included for our (human) benefit.

Perhaps it's a permissions issue, although I don't see how since I doubt the first stage of grub2 understands such minutia.

I rebooted after the update to make sure that my grub was working as expected with the older 05_debian file--it is & this is it--take a look Nate & see if it differs majorly from yours.


I'm hoping to have the GFX menu up soon--will report with progress....

---

### Post by dinxter on 2009-08-11
i've stuck the gfxmenu enabled version of uptodate grub2 im using in [https://launchpad.net/~dinxter/+archive/experimental](https://launchpad.net/~dinxter/+archive/experimental)
also a small package of themes from gibibit and [http://hateanthem.dreamhosters.com/arch/build/](http://hateanthem.dreamhosters.com/arch/build/), hope they dont mind. the ppa is temporary and for playing only :) please don't use it unless you dont mind a very broken computer that doesnt boot
i do have a problem with slow redrawing of menus on gfxmenu but apart from that it works ok, but then, i've had the chronically slow scrolling of the command line grub2 bug for a while now so that might just be related to that.

---

### Post by dinxter on 2009-08-11
oh, and if anyone knows of a way to retroactively add the --class options to meneentries generated by the previous scripts in grub.d? i dont want to hack the grub packaged scripts if possible to avoid all the messing around on updates, if theres a way to have later scripts access the parts of grub.cfg generated by the previous ones that would be good

---

### Post by Nate B. on 2009-08-11
I guess that a splash image simply won't work on my laptop (Thinkpad T41).  I went back to modifying the 05_debian_theme file and enabled it by making it executable and removed the exec bits from my custom file.  Here is the extent of my changes:

```
$ diff -u 05_debian_theme.orig 05_debian_theme
--- 05_debian_theme.orig        2009-08-10 07:17:00.000000000 -0500
+++ 05_debian_theme     2009-08-11 06:05:54.000000000 -0500
@@ -5,15 +5,15 @@
 set_mono_theme()
 {
   cat << EOF
-set menu_color_normal=white/black
-set menu_color_highlight=black/white
+set menu_color_normal=cyan/blue
+set menu_color_highlight=white/blue
 EOF
 }

 # check for usable backgrounds
 use_bg=false
 if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
-  for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga} ; do
+  for i in {/boot/grub,/usr/share/images/desktop-base}/linuxinside.{png,tga} ; do
     if is_path_readable_by_grub $i ; then
       bg=$i
       case ${bg} in

```

As you can see, very minimal changes, cosmetic only.

While editing /etc/default/grub to re-enable the grub menu I found the following lines:

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

```

I uncommented the last line and still no Grub splash screen.

Then I broke it!  :lolflag:

I ran the vbeinfo command from the grub menu screen and it only showed 400x300 being a usable screen resolution.  So I set ```
GRUB_GFXMODE=400x300
``` and resized my image to 400x300.  Well, I still had no splash image and I also had no bootable menu entries.  D'oh!  I wound up having to start the Kubuntu CD in live mode and edit crug.cfg since update-grub would not work even after doing a chroot command just to restore order.  I've since set ```
GRUB_GFXMODE=640x480
``` and put my 640x480 image into /boot/grub and I'm back to square one.

I've attached my grub.cfg which seems to be nothing unusual.

---

### Post by dinxter on 2009-08-11
seems gfxmenu theming can be a bit tricky, themes dont scale well ( by pixel placement ) but i'm liking the circular timer :) this ones the xsplash background

---

### Post by autocrosser on 2009-08-11
That's nice Dinxter!!!! I ended up doing work-related stuff last night & most likely will tonight too :confused: --got a website to un-muck-up.......

Nate--I don't know where to go next--I don't suppose you would want to do a reinstall :( , but I would recommend waiting for the next Alpha--and then think about it. Hmmm--I do note that your 30 line is "### BEGIN /etc/grub.d/30_otheros ###"--the stock one is "### BEGIN /etc/grub.d/30_os-prober ###" I'm going to include my grub.cfg for you to look at......

---

### Post by phenest on 2009-08-11
> **Nate B. said:**
> ... and still no Grub splash screen.

I don't suppose it's the image you're using? I can't make any of my custom ones to work either, but the ones in the grub2-splashimages package work a treat.

---

### Post by wayne_cat on 2009-08-11
dinxter,

I had no luck ... I can compile the patched grub2 version if I activate the the test functions ... and it works well ... but dpkg-buildpackage fails. 

```
grub_vbe_bios_set_display_start in videotest is not defined
make[1]: *** [moddep.lst] Error 1
make[1]: Leaving directory `/home/rschmitt/Desktop/build/grub2-1.96+20090725/build/grub-coreboot'
make: *** [build/grub-coreboot] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
rschmitt@macbook:~/Desktop/build/grub2-1.96+20090725$ 
```

---

### Post by dinxter on 2009-08-11
> **wayne_cat said:**
> dinxter,

I had no luck ... I can compile the patched grub2 version if I activate the the test functions ... and it works well ... but dpkg-buildpackage fails. 

```
grub_vbe_bios_set_display_start in videotest is not defined
make[1]: *** [moddep.lst] Error 1
make[1]: Leaving directory `/home/rschmitt/Desktop/build/grub2-1.96+20090725/build/grub-coreboot'
make: *** [build/grub-coreboot] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
rschmitt@macbook:~/Desktop/build/grub2-1.96+20090725$ 
```

yep, thats exactly the problem with keeping grub_vbe_bios_set_display_start in. you can see why i thought it was something in debian/ packaging, it 'makes' fine but won't 'debuild' without that error

---

### Post by wayne_cat on 2009-08-11
> **dinxter said:**
> yep, thats exactly the problem with keeping grub_vbe_bios_set_display_start in. you can see why i thought it was something in debian/ packaging, it 'makes' fine but won't 'debuild' without that error

Fortunately the functions are not critical

---

### Post by dinxter on 2009-08-11
been having some trouble loading fonts with gfxmenu, i dont know if somethings changed or something i've been messing about with :) 
leaves it unbootable so i've had to disable my grub.d script. just a warning should anyone else be using it and gets the same

---

### Post by dinxter on 2009-08-11
i stand corrected, its not gfxmenu but something related to the new gdm/xsplash work. it still boots fine, when i've got splash enabled i can see that now :) tty's are disabled somehow too

---

### Post by Nate B. on 2009-08-12
> **phenest said:**
> I don't suppose it's the image you're using? I can't make any of my custom ones to work either, but the ones in the grub2-splashimages package work a treat.

My custom file is a PNG conversion of a pixmap that worked flawlessly with grub-legacy.  I tried one of the images included in the grub2-splashimages package, the B1B one, which didn't work either.  I suppose I can try another, but I doubt they'll work on this either.

Autocrosser, the 30_otheros file is where I manually define my Puppy installation as that is not identified by the osprober file.  A complete reinstallation of Kubuntu isn't going to solve the problems in one package, IMO.  As Grub2 is probably still in heavy development, I'm not going to worry about this very much as I'm convinced that its a simple incompatibility with my video hardware in this laptop.  If I wasn't rebooting between Kubuntu and Sid so often, I wouldn't even see the Grub screen as I mostly suspend to RAM.

---

### Post by Starks on 2009-08-12
I got the graphical boot working, but the text ubuntuglow stuff flashes.

Also, how do I change my gfxmenu theme without having my grub.cfg wiped?

---

### Post by autocrosser on 2009-08-12
Well--hang in there--I keep a eye on grub2 development list, so I'll post if anything looks interesting...


> **Nate B. said:**
> My custom file is a PNG conversion of a pixmap that worked flawlessly with grub-legacy.  I tried one of the images included in the grub2-splashimages package, the B1B one, which didn't work either.  I suppose I can try another, but I doubt they'll work on this either.

Autocrosser, the 30_otheros file is where I manually define my Puppy installation as that is not identified by the osprober file.  A complete reinstallation of Kubuntu isn't going to solve the problems in one package, IMO.  As Grub2 is probably still in heavy development, I'm not going to worry about this very much as I'm convinced that its a simple incompatibility with my video hardware in this laptop.  If I wasn't rebooting between Kubuntu and Sid so often, I wouldn't even see the Grub screen as I mostly suspend to RAM.

---

### Post by autocrosser on 2009-08-12
> **Starks said:**
> I got the graphical boot working, but the text ubuntuglow stuff flashes.

Also, how do I change my gfxmenu theme without having my grub.cfg wiped?


Are you using the 41_gfxmenu? If so, you can comment out & add in themes...relevant area```
# Set the initial gfxmenu theme.
theme="/boot/grub/themes/ubuntu2/theme.txt"
#theme="/boot/grub/themes/ubuntu1/theme.txt"
#theme="/boot/grub/themes/winter/theme.txt"
#theme="/boot/grub/themes/proto/theme.txt"
#theme="/boot/grub/themes/ubuntuglow/theme.txt"; gfxmode="1024x768"
```

---

### Post by dinxter on 2009-08-12
> **Starks said:**
> I got the graphical boot working, but the text ubuntuglow stuff flashes 
yep, i get that too, not sure if its a gfxmenu bug or not. just because all versions of grub2 so far in karmic (unpatched ones) have chronic refresh problems too, if i go to the command line and fill it up  with enough text to cause it to scroll. enter 'help' a couple of times and you might see the same thing. 
at the moment i'm using 41_gfxmenu in grub.d that looks like below. just changing the theme and the resolution at the top and running update-grub is enough to change the theme. note i think the developer is looking to add theme changing to gfxmenu itself at some point. 
still trying to get a non intrusive way to add the --class options to menuentries, so you get nice icons to go with it all, without having it in scripts that are overwritten when grub updates
```

#! /bin/sh -e
# choose theme and resolution
THEME="/boot/grub/themes/ubuntu-karmic/theme.txt"
RESOLUTION="1024x768"

echo "Enabling gfxmenu support..." >&2
FONT_DIR="/boot/grub/fonts/"
#fallback if theme not found
if [ ! -e $THEME ] ; then
    THEME="/boot/grub/themes/ubuntu1/theme.txt"
    echo "Chosen theme doesn't exist! setting to default..." >&2
fi
cat<<EOF
insmod biosdisk
insmod pc
insmod font
insmod vbe
insmod gfxterm
insmod videotest
insmod tga
insmod png
insmod gfxmenu

menuviewer="gfxmenu"

gfxmode="$RESOLUTION"
theme="${THEME}"
EOF
#collect fonts
for file in `find ${FONT_DIR} -name *pf2`
do
    echo "loadfont $file"
done
```
[EDIT] sorry a bit of a typo, DEFAULT_THEME variable should have been THEME. distracted by the death of a hard drive :)

---

### Post by autocrosser on 2009-08-12
> **dinxter said:**
> <SNIP>[EDIT] sorry a bit of a typo, DEFAULT_THEME variable should have been THEME. distracted by the death of a hard drive :)

Yes--that is all the rage right now :P

I feel slighted in that all mine are new enough that I can't "share the love":lolflag:

---

### Post by dinxter on 2009-08-12
> **autocrosser said:**
> Yes--that is all the rage right now :P

I feel slighted in that all mine are new enough that I can't "share the love":lolflag:

ironically it wasnt the one that for over a year has taken 5 mins to startup due to it clicking away, thats still fine. nor was it either of the 2 that palimpsest is convinced should be binned. no, its the one drive that no-one suspected! i get the feeling i might need to invest in a new computer soon :)

---

### Post by dinxter on 2009-08-13
quick script for renaming or deleting menu entries generated by grub if anyone wants to use or preferebly make a better one!

/etc/grub.d/42_menu_alias (executable)
```
#! /bin/sh
MENU_ALIASES="/etc/grub.d/menu_aliases"
GRUB_CFG_TEMP="/boot/grub/grub.cfg.new"

while read line
do
    FIRST=`echo $line| cut -d"|" -f1`
    SECOND=`echo $line | cut -d "|" -f2`
    if [ ! "$SECOND" = "\"\"" ] ; then
    echo ""
        sed -i "s|^\(menuentry.*\)$FIRST\(.*\){|\1$SECOND\2{|g" $GRUB_CFG_TEMP
    else
        FIRST_LINE=`grep -n -e"^\(menuentry.*\)$FIRST\(.*\){" $GRUB_CFG_TEMP\
                     |cut -d":" -f1`
    
    sed -i "$FIRST_LINE,/}/d" $GRUB_CFG_TEMP
    fi
done < $MENU_ALIASES
```then stick aliases in the file (non-executable) below, in the format 
"grub boot entry"|"new name"
if the new name is "" then the entire menu entry will be hidden. note this is a quick and rough go so you might want to check your grub.cfg isnt garbled afterwards :) works for me though,and wont be overwritten on grub updates

/etc/grub.d/menu_aliases (non-executable)
```
"Ubuntu, Linux 2.6.31-5-generic"|"Karmic Koala"
"Ubuntu, Linux 2.6.31-5-generic (recovery mode)"|""  
"Microsoft Windows XP Professional (on /dev/sdd1)"|"Windows XP"
"Ubuntu karmic (development branch), memtest86+ (on /dev/sdd2)"|"" 
```

---

### Post by dinxter on 2009-08-13
along the same simple and perhaps a little too casual approach to search and replace, if your using gfxmenu and want some pretty little icons to go with you now possibly nicely renamed menus, try adding the following lines to the bottom of your gfxmenu script. note, i can only say that the first 2 actually work

```
GRUB_CFG_TEMP="/boot/grub/grub.cfg.new"
sed -i "s|^\(menuentry.*Windows.*\){|\1 --class windows --class os {|g" $GRUB_CFG_TEMP
sed -i "s|^\(menuentry.*Ubuntu.*\){|\1 --class ubuntu --class linux --class os {|g" $GRUB_CFG_TEMP
sed -i "s|^\(menuentry.*Debian.*\){|\1 --class debian --class linux --class os {|g" $GRUB_CFG_TEMP
sed -i "s|^\(menuentry.*Kubuntu.*\){|\1 --class kubuntu --class linux --class os {|g" $GRUB_CFG_TEMP
sed -i "s|^\(menuentry.*Gentoo.*\){|\1 --class gentoo --class linux --class os {|g" $GRUB_CFG_TEMP
sed -i "s|^\(menuentry.*OpenSUSE.*\){|\1 --class opensuse --class linux --class os {|g" $GRUB_CFG_TEMP


```

---

### Post by Starks on 2009-08-13
Nice.

Are you going to add these changes to the PPA?

---

### Post by dinxter on 2009-08-13
i'll hopefully update the ppa over the weekend and maybe gather together some generally useful grub2 scripts (and tidy up the ones i'm using) in a new package over the weekend

---

### Post by Starks on 2009-08-13
I hope that graphical grub will make it into Lucky Liger or Mellow Moose.

---

### Post by dinxter on 2009-08-13
the plan seems to be to integrate an os-chooser into xsplash, which could be very good since that would have all the facilities of an X stack to work with so it could look spectacular. i'm still a little confused to how that will work in practice but we will see. no matter what, gfxmenu will be mainlined into grub at some point, and rightly so, i've never seen my boot screen look so good!

---

### Post by wayne_cat on 2009-08-13
> **dinxter said:**
> the plan seems to be to integrate an os-chooser into xsplash, which could be very good since that would have all the facilities of an X stack to work with so it could look spectacular. i'm still a little confused to how that will work in practice but we will see. no matter what, gfxmenu will be mainlined into grub at some point, and rightly so, i've never seen my boot screen look so good!

this is maybe interesting ... last month:

[http://lists.gnu.org/archive/html/grub-devel/2009-07/msg00319.html](http://lists.gnu.org/archive/html/grub-devel/2009-07/msg00319.html)

```
We need two-level menu. **However I prefer to merge gfxmenu first**.
```

---

### Post by ranch hand on 2009-08-13
> **Starks said:**
> I hope that graphical grub will make it into Lucky Liger or Mellow Moose.
Lusty Lemming

---

### Post by wayne_cat on 2009-08-13
> **ranch hand said:**
> Lusty Lemming


no way ... it will be **censored** **censored**

---

### Post by kingborel on 2009-08-13
> **wayne_cat said:**
> no way ... it will be **censored** **censored**

Leisure-suit Larry?

---

### Post by autocrosser on 2009-08-13
That is SO 80's:P:P:P

How about Laudable Lemur????

Levitating Lark----Languishing Lhasa Apso---Leaping Lionfish--Lively Lobster---Livid Lama---Loquacious Lizard---Lyrical Lorikeet??????

:lolflag::lolflag::lolflag:

---

### Post by Nate B. on 2009-08-14
Lucky Llama?

---

### Post by dinxter on 2009-08-15
added icon finding to ppa, if you use the menu renaming script too it should end up looking something like mine below

---

### Post by billak on 2009-08-15
Nice job !!! How didi you do that? Could you please post some details?

---

### Post by autocrosser on 2009-08-15
> **dinxter said:**
> added icon finding to ppa, if you use the menu renaming script too it should end up looking something like mine below


Could you post your PPA? Thanks Dinxter!!!

---

### Post by wayne_cat on 2009-08-15
> **autocrosser said:**
> Could you post your PPA? Thanks Dinxter!!!

[https://launchpad.net/~dinxter/+archive/experimental](https://launchpad.net/~dinxter/+archive/experimental)

---

### Post by wayne_cat on 2009-08-15
> **dinxter said:**
> i've stuck the gfxmenu enabled version of uptodate grub2 im using in [https://launchpad.net/~dinxter/+archive/experimental]("https://launchpad.net/%7Edinxter/+archive/experimental")
also a small package of themes from gibibit and [http://hateanthem.dreamhosters.com/arch/build/](http://hateanthem.dreamhosters.com/arch/build/), hope they dont mind. the ppa is temporary and for playing only :) please don't use it unless you dont mind a very broken computer that doesnt boot
i do have a problem with slow redrawing of menus on gfxmenu but apart from that it works ok, but then, i've had the chronically slow scrolling of the command line grub2 bug for a while now so that might just be related to that.

I have the same problem ... redrawing is really slow and the GPU or CPU usages seems
to be very high (the fans of my notebook are a good indicator).

---

### Post by dinxter on 2009-08-15
that menu_alias script is truly terrible! i should really learn how to use awk, and bash, and the rest :) works after a fashion though :)
there was a bunch of framebuffer/vbe stuff in svn [2494]("http://svn.savannah.gnu.org/viewvc?view=rev&root=grub&revision=2494") which may or not make a difference, compiles and packages fine but i can't be bothered bodging gfxmenu into a working patch at the moment, let alone any of the many debian/ubuntu patches that break ) so i'm not sure if it'll help the redrawing problem. maybe next week, if it rains alot...

---

### Post by Starks on 2009-08-16
Can the kernel line be edited before booting in gfxmenu?

---

### Post by dinxter on 2009-08-16
> **Starks said:**
> Can the kernel line be edited before booting in gfxmenu?
doesnt seem so, but you can switch to a text menu by pressing 't' and do that. 
the keys i remember are,
't' - text menu
't' then 'c' - grub console
'1' to '4' - show the 4 default themes

---

### Post by celticbhoy on 2009-08-16
I have to say dinxter - those startups look fantastic compared to normal grub. I have grub2 installed and so far I have only been able to change the background, resolution & text colours. I have read through this thread & to be honest I cant seem to follow the thread to achieve what you have managed, would it be possible to laydown all the steps involved in one post?

---

### Post by dinxter on 2009-08-16
> **celticbhoy said:**
> I have to say dinxter - those startups look fantastic compared to normal grub. I have grub2 installed and so far I have only been able to change the background, resolution & text colours. I have read through this thread & to be honest I cant seem to follow the thread to achieve what you have managed, would it be possible to laydown all the steps involved in one post?

i was using my ppa really as a play area for gfxmenu and not too useful for anyone else, i'll try and tidy it up this evening or more likely start of next week so its easier to use and less 'breaky'
* rename grub-pc to grub-gfxmenu to emphasise the breakiness of the package
* move scripts to a grub-custom-scripts package with
        - set/enable gfxmenu theme
        - replace background image
        - rename/remove menu entries
     - maybe some more if i can think of any
* grub-gfxmenu-themes with some slightly broken themes in it

after thats done you should just be able to enable themes in 50_grub-custom scripts and have it work without too much danger. the one i'm using at the moment has 
rename_menu "Memory test (memtest86+, serial console 115200) (on /dev/sdd2)" ""

set_background "/usr/share/images/grub/BonsaiTridentMaple.tga"

set_gfxmenu_theme "/boot/grub/themes/ubuntu-karmic/theme.txt"

which all work fine-ish for me at the moment. as i say i'll try to that soon since it will be simple to use for other people who might want to use it
note though,
* make sure you know how to recover a broken grub! and replace the gfxmenu package with the grown up grub-pc from the repository
* gfxmenu is not in grub yet and has some problems
     - themes dont scale well and some fonts arent right
     - slow drawing refresh rates

---

### Post by celticbhoy on 2009-08-16
Still must be looking in the wrong places could you post your grub.cfg, grub.d & /etc/default/grub files please.

---

### Post by haider_up32 on 2009-08-16
> **MacUntu said:**
> Had to reinstall GRUB2 to get the background working:

[[img]http://img.xrmb2.net/771492.jpg[/img]](http://img.xrmb2.net/images/771492.png)

And now I want a seamless transition to GDM. :P

Are there any known image property limits (like colors, size, ...)?

can u upload the splash image and whats the process of adding it to GRUB

---

### Post by dinxter on 2009-08-17
hopefully messing about with gfxmenu should be pretty straightforward now. usual warnings about knowing how to recover grub apply :*)
1. add [Kaboom! ppa]("https://launchpad.net/%7Edinxter/+archive/experimental")
2. install the gfxmenu enabled grub-pc, grub-themes-gfxmenu and grub-custom-scripts
3. edit 50_grub-custom-scripts, uncommenting and editing the examples there as needed then run update-grub. 
uncommenting set_gfxmenu_theme will enable gfxmenu (note the resolution is set in /etc/default/grub, most of the themes are best at 1024x768 , as is disabling the hidden timeout so you actually see the grub menu ). if you want to rename/delete menu entries note that these can be found in /boot/grub/grub.cfg or even
```
cat /boot/grub/grub.cfg|grep menuentry|cut -d"\"" -f2
```:)

---

### Post by dinxter on 2009-08-17
just to add, you can install grub-custom-scripts with the main karmic, non gfxmenu hacked version of grub-pc if you want to rename entries/set background with that

---

### Post by autocrosser on 2009-08-17
Dinxter--running into a problem---terminal output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-gfxmenu-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grub-gfxmenu-pc has no installation candidate

```

Looks like I've hit a "interesting" bit....the gfxmenu versions are "installed" but not installed...

```
Setting up grub-pc (1.96+20090725-1ubuntu3~dinxter2) ...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-6-generic
Found initrd image: /boot/initrd.img-2.6.31-6-generic
Found linux image: /boot/vmlinuz-2.6.31-5-generic
Found initrd image: /boot/initrd.img-2.6.31-5-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu karmic (development branch) (9.10) on /dev/sdb1
Found Ubuntu 9.04 (9.04) on /dev/sdc1
Found Ubuntu 9.04 (9.04) on /dev/sdd3
/etc/grub.d/50_grub-custom-scripts.dpkg-new: line 2: /etc/grub.d/grub-custom-scripts_lib: No such file or directory
/etc/grub.d/50_grub-custom-scripts.dpkg-new: line 6: rename_menu: command not found
/etc/grub.d/50_grub-custom-scripts.dpkg-new: line 9: rename_menu: command not found
/etc/grub.d/50_grub-custom-scripts.dpkg-new: line 12: rename_menu: command not found
/etc/grub.d/50_grub-custom-scripts.dpkg-new: line 19: set_gfxmenu_theme: command not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of grub-custom-scripts:
 grub-custom-scripts depends on grub-pc | grub-gfxmenu-pc; however:
  Package grub-pc is not configured yet.
  Package grub-gfxmenu-pc is not installed.
dpkg: error processing grub-custom-scripts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-themes-gfxmenu:
 grub-themes-gfxmenu depends on grub-pc | grub-gfxmenu-pc; however:
  Package grub-pc is not configured yet.
  Package grub-gfxmenu-pc is not installed.
 grub-themes-gfxmenu depends on grub-custom-scripts; however:
  Package grub-custom-scripts is not configured yet.
dpkg: error processing grub-themes-gfxmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub2:
 grub2 depends on grub-pc; however:
  Package grub-pc iNo apport report written because the error message indicates its a followup error from a previous failure.

```


I would say that I'm not rebooting anytime soon :):):)

Ideas?

---

### Post by autocrosser on 2009-08-17
Fixed my own problem--as I saw that grub-pc was the problem, I unpacked & hand-installed it to the correct places..as soon as I did that the install "unstuck" itself & went forward normally--not the most orthodox install---but it works OK.....as least as far as being installed---now to reboot & see :P

---

### Post by Starks on 2009-08-18
Note to self: Manually removing the grub2 scripts in /etc/grub.d/ will prevent them from being easily restored.

---

### Post by cecilpierce on 2009-08-18
Whats causing the flashing and half the theme is off the screen like its too big ! 640X480 now, I tried 1040X768 and got no grub at all. Had to boot from a flash drive, bummer...

---

### Post by autocrosser on 2009-08-18
Yes--my luck was rather mixed also--I could boot with no menu at 640x480, 800x600 & 1024x768---as soon as I tried a native resolution for my monitor (1440x900), grub locked up tight--popped in a Live & chrooted in to fix things...too much fun for one night--need to do some more checking before I do that again :)--I just downgraded & locked until I know more........

---

### Post by dinxter on 2009-08-18
> **autocrosser said:**
> Dinxter--running into a problem---terminal output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-gfxmenu-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grub-gfxmenu-pc has no installation candidate

```

doh! was going to rename the grub-pc package but was too lazy in the end, should be ok when the new packages build, sorry, its was a monday thing :)

---

### Post by Starks on 2009-08-18
dinxter, I don't think your packages install 41_gfxmenu anymore.

---

### Post by dinxter on 2009-08-18
> **Starks said:**
> dinxter, I don't think your packages install 41_gfxmenu anymore.
i've got rid of 41_gfxmenu and now it should install a file 50_grub_custom_scripts with a file grub-custom-scripts which means you can add options to 50_grub-custom-scripts like,

set_background "gfxterm background filename"
rename_menu "old name" "new name"
set_gfxmenu_theme "path to gfxmenu theme"

which should be easier to fiddle with,  mine looks like

```
#!/bin/bash 
. /etc/grub.d/grub-custom-scripts_lib

## Set the background for gfxterm
set_background "/usr/share/images/grub/BonsaiTridentMaple.tga"

## Enable gfxmenu and set the theme
set_gfxmenu_theme "/boot/grub/themes/ubuntu-karmic/theme.txt"

rename_menu "Ubuntu, Linux 2.6.31-6-generic" "Karmic Koala"
 rename_menu "Ubuntu, Linux 2.6.31-6-generic (recovery mode)" ""
 rename_menu "Microsoft Windows XP Professional (on /dev/sdd1)" "Windows XP"
 rename_menu "Ubuntu, Linux 2.6.31-5-generic (on /dev/sdd2)" "Ubuntu Backup"
 rename_menu "Ubuntu, Linux 2.6.31-5-generic (recovery mode) (on /dev/sdd2)" ""
 rename_menu "Memory test (memtest86+) (on /dev/sdd2)" ""
 rename_menu "Memory test (memtest86+, serial console 115200) (on /dev/sdd2)" ""

```

---

### Post by autocrosser on 2009-08-18
Could you post when the packages are rebuilt?  Want to try again with the correct resolution.....Your option is much better than me hand-building my own (and easier to recover after :P ).......

---

### Post by skylen on 2009-08-18
Hi,

As the author of the GRUB 2 graphical menu, I thought I should hang out in this thread a bit and perhaps provide some help and/or information.

> **dinxter said:**
> yep, i get that too, not sure if its a gfxmenu bug or not. just because all versions of grub2 so far in karmic (unpatched ones) have chronic refresh problems too


Yes, I don't know why the double-buffering is not providing consistently smooth screen updates.  In my testing during development of gfxmenu last summer, I experienced very smooth updates with no flickering, but for some reason VBE page-flipping may not be working completely right on all hardware.  This needs some troubleshooting to understand the problem, and I just haven't had a chance to do it yet.

> **dinxter said:**
>  
at the moment i'm using 41_gfxmenu in grub.d that looks like below. just changing the theme and the resolution at the top and running update-grub is enough to change the theme. note i think the developer is looking to add theme changing to gfxmenu itself at some point. 


Yes, it is a fairly high priority item in my mind to add a runtime theme switching menu to GRUB.  I imagine a little pop-up menu that allows switching themes easily.

Cheers,
Colin

---

### Post by skylen on 2009-08-18
> **dinxter said:**
> 
* gfxmenu is not in grub yet and has some problems
     - themes dont scale well and some fonts arent right
     - slow drawing refresh rates

Those are very good points, and they are ones which bother me as well–I definitely want to get them resolved.  I really want to polish the graphical menu interface but other obligations in life have kept me too busy for the past months.  Fortunately, another GRUB developer, Vladimir ‘phcoder’ Serbinenko, has been really helpful in helping to get gfxmenu ready for inclusion into GRUB's mainline.  It should happen very soon.

Cheers,
Colin

---

### Post by dinxter on 2009-08-18
> **autocrosser said:**
> Could you post when the packages are rebuilt?  Want to try again with the correct resolution.....Your option is much better than me hand-building my own (and easier to recover after :P ).......
from, 
grub-custom-scripts-0.1-1~dinxter5 and
grub-themes-gfxmenu-0.1-3~0ubuntu0~dinxter14
( i just noticed the messed up versioning on these! )
onwards they should just depend on grub-pc, renaming grub-pc is probably a good idea but its more bother thans worth i think. i'll probably leave grub-pc unless theres some big update to grub or gfxmenu or something, and leave the themes as they are, broken fonts and all, unless anyone has some cool ones to add :) 
Might mess about more with the custom scripts one  but just try and add anymore useful options i stumble across during tinkering or fix the ones currently there

---

### Post by dinxter on 2009-08-18
> **skylen said:**
> Those are very good points, and they are ones which bother me as well–I definitely want to get them resolved.  I really want to polish the graphical menu interface but other obligations in life have kept me too busy for the past months.  Fortunately, another GRUB developer, Vladimir ‘phcoder’ Serbinenko, has been really helpful in helping to get gfxmenu ready for inclusion into GRUB's mainline.  It should happen very soon.

Cheers,
Colin

looking forward to it reaching grub trunk, and thanks to all for the efforts, it's looking good

---

### Post by ranch hand on 2009-08-18
> **skylen said:**
> Hi,

As the author of the GRUB 2 graphical menu, I thought I should hang out in this thread a bit and perhaps provide some help and/or information.



Yes, I don't know why the double-buffering is not providing consistently smooth screen updates.  In my testing during development of gfxmenu last summer, I experienced very smooth updates with no flickering, but for some reason VBE page-flipping may not be working completely right on all hardware.  This needs some troubleshooting to understand the problem, and I just haven't had a chance to do it yet.



Yes, it is a fairly high priority item in my mind to add a runtime theme switching menu to GRUB.  I imagine a little pop-up menu that allows switching themes easily.

Cheers,
Colin
As an infatuated lover of grub-legacy I must thank you for your efforts on grub2.  I have been taken a LONG way down the road to changing my love to grub2.

As far as I am concerned, you have the foundation for a GREAT boot manager.  Let us keep it that way and worry about the function of it first.

These guys are doing some nice things for looks as it is.  I would like it to pick up all my 9.10 installs correctly and my Mandrivas and I believe there are problems with some other OS'.

Custom entries are handling the job but the "prober" weakness', in my opinion, are way more important than how the bugger looks.  I probably have to look at it longer and more often than most users.

Right now I have 2 drives booting from grub2.  One has 11 OS' and the other has 8.

---

### Post by autocrosser on 2009-08-18
THANK YOU for posting in!!! It is very nice to have the developer in as we work thru how this works....Do you have a timeline on inclusion & do you think that Vladimir would be interested in posting in also?  I for one would like to really be on top of where this is going :)

> **skylen said:**
> Hi,

As the author of the GRUB 2 graphical menu, I thought I should hang out in this thread a bit and perhaps provide some help and/or information.



Yes, I don't know why the double-buffering is not providing consistently smooth screen updates.  In my testing during development of gfxmenu last summer, I experienced very smooth updates with no flickering, but for some reason VBE page-flipping may not be working completely right on all hardware.  This needs some troubleshooting to understand the problem, and I just haven't had a chance to do it yet.



Yes, it is a fairly high priority item in my mind to add a runtime theme switching menu to GRUB.  I imagine a little pop-up menu that allows switching themes easily.

Cheers,
Colin

---

### Post by autocrosser on 2009-08-18
> **ranch hand said:**
> As an infatuated lover of grub-legacy I must thank you for your efforts on grub2.  I have been taken a LONG way down the road to changing my love to grub2.

As far as I am concerned, you have the foundation for a GREAT boot manager.  Let us keep it that way and worry about the function of it first.

These guys are doing some nice things for looks as it is.  I would like it to pick up all my 9.10 installs correctly and my Mandrivas and I believe there are problems with some other OS'.

Custom entries are handling the job but the "prober" weakness', in my opinion, are way more important than how the bugger looks.  I probably have to look at it longer and more often than most users.

Right now I have 2 drives booting from grub2.  One has 11 OS' and the other has 8.

Those are valid points--but this thread is about theming Grub2. skylen is the developer for the menu & as such--most likely does not have much input on other usability functions in Grub2.....I follow the Grub2 development list & can post how you can join it to work with those problems......I'm very sure that skylen wants to be involved with what we are doing here.

---

### Post by dinxter on 2009-08-18
one thing i've done this evening, tried to remove ugly picket fence hack from rename_menu
> MENU_OLD=`echo $MENU_OLD|sed  "s/\//\\\./g"`
 sed -i "s/^\(menuentry.*\"\)$MENU_OLD\(\".*\){/\1$MENU_NEW\2{/g" $GRUB_CFG_TEMPis now simplified to,
 > sed -i "s|^\(menuentry.*\"\)$MENU_OLD\(\".*\){|\1$MENU_NEW\2{|g" $GRUB_CFG_TEMPgood grief :)
upshot is '/' in renaming is ok without hacking it about, but '|' is a no-no in menu names...

---

### Post by dinxter on 2009-08-19
sunset-ish  with basic menu and select, all it needs now is sides to them :) then i might add it to the themes, i'm beyond the file size to upload

---

### Post by celticbhoy on 2009-08-19
gary@Testing:~$ sudo update-grub
[sudo] password for gary: 
Generating grub.cfg ...
Found Debian background: Reve.tga
Found linux image: /boot/vmlinuz-2.6.31-6-generic
Found initrd image: /boot/initrd.img-2.6.31-6-generic
Found linux image: /boot/vmlinuz-2.6.31-5-generic
Found initrd image: /boot/initrd.img-2.6.31-5-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.04 (9.04) on /dev/sda1
Found Windows Vista (loader) on /dev/sda3
Found Moblin release 2.0 (Moblin) on /dev/sda7
sed: -e expression #1, char 1: unknown command: `,'
gary@Testing:~$ 


How do I find out what config file is causing this error?

---

### Post by dinxter on 2009-08-19
its looks like the problem with regular expression expansion in sed when renaming menu entries, try the latest version, in theory as long as the menuentry doesnt contain a '|' character the [        grub-custom-scripts - 0.1-1-0ubuntu0~dinxter8scripts]("https://launchpad.net/%7Edinxter/+archive/experimental/+sourcepub/702301/+listing-archive-extra") should work fine. the newer versions also give more information about whats failing. also, debugging shell scripts can be done by adding set -x to any of the scripts in grub.d

---

### Post by celticbhoy on 2009-08-19
When I try and install the themes I get this :-


E: linux-image-2.6.31-6-generic: subprocess installed post-installation script returned error exit status 1
E: grub-pc: subprocess installed post-installation script returned error exit status 1
E: grub-custom-scripts: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: grub-themes-gfxmenu: dependency problems - leaving unconfigured

I think I should maybe completely purge grub2 & re-install - any advice on the best way to accomplish this.

---

### Post by dinxter on 2009-08-19
> **celticbhoy said:**
> When I try and install the themes I get this :-


E: linux-image-2.6.31-6-generic: subprocess installed post-installation script returned error exit status 1
E: grub-pc: subprocess installed post-installation script returned error exit status 1
E: grub-custom-scripts: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: grub-themes-gfxmenu: dependency problems - leaving unconfigured

I think I should maybe completely purge grub2 & re-install - any advice on the best way to accomplish this.
  
you can purge grub by
1. dpkg --purge --force-all grub-pc grub-common
2. disable the gfxmenu repository
3. apt-get update
4 apt-get install grub-pc

i would add though that this doesnt seem to be your problem, the problem seems to be 
linux-image-2.6.31-6-generic fails, this causes  grub-pc to fail, and as a result of this grub-custom-scripts fails. you probably need to sort out why linux-image-2.6.31-6-generic fails and then the rest of the packages should install properly

---

### Post by dinxter on 2009-08-19
note, you can turn on dpkg debugging to see the problems when installing, see dpkg --debug=help for more. you can also see more debugging info by adding '-x' to bash scripts, for dpkg these are in /var/lib/info/dpkg/ for example, adding 'set -x' to grub-pc.postinst will show all the commands executed and hopefully show the failure point

---

### Post by celticbhoy on 2009-08-19
As I installed from your PPA on the same day & at roughly the same time as the new kernel updated I presumed it was the new grub that had a problem with my machine - sorry.

---

### Post by dinxter on 2009-08-19
> **celticbhoy said:**
> As I installed from your PPA on the same day & at roughly the same time as the new kernel updated I presumed it was the new grub that had a problem with my machine - sorry.
no need to apologise, its entirely possible! but the fact that the linux image is failing possibly suggests otherwise, the gfxmenu patched grub-pc package uses the same scripts as the original and doesnt actually do anything too different from the repository version. and the grub-custom-scripts and grub-themes-gfxmenu packages are pretty trivial, they only use basic debian helper scripts to install a few files and do nothing fancy. it still could be the ppa packages though

---

### Post by curley_sue on 2009-08-19
> **dinxter said:**
> hopefully messing about with gfxmenu should be pretty straightforward now. usual warnings about knowing how to recover grub apply :*)
1. add [Kaboom! ppa]("https://launchpad.net/%7Edinxter/+archive/experimental")
2. install the gfxmenu enabled grub-pc, grub-themes-gfxmenu and grub-custom-scripts
3. edit 50_grub-custom-scripts, uncommenting and editing the examples there as needed then run update-grub. 
uncommenting set_gfxmenu_theme will enable gfxmenu (note the resolution is set in /etc/default/grub, most of the themes are best at 1024x768 , as is disabling the hidden timeout so you actually see the grub menu ). if you want to rename/delete menu entries note that these can be found in /boot/grub/grub.cfg or even
```
cat /boot/grub/grub.cfg|grep menuentry|cut -d"\"" -f2
```:)
Thank you dinxter for making the installation process relatively simple.

I would like to note two things regarding this procedure:

1)on a fresh install of Karmic (from yesterday) - the installation described in #131 gave configuration errors (in synaptic).
This was solved (finally) by purging (not just removing) all grub related packs and only then, installing them following the instructions in #131 (quoted above).

2) this was more than worthwhile as till that point I could not have my tty (non-graphical consoles).

done on thinkpad t61+NVIDIA Quadro NVS 140M. 
in /etc/default/grub:
GRUB_GFXMODE=1440x900x32

todo: get the correct resolution in the tty's (currently they are too big)
could this be done as in previous ubuntu versions (such as jaunty), following:
[http://ubuntuforums.org/showthread.php?t=622018](http://ubuntuforums.org/showthread.php?t=622018)
?

---

### Post by dinxter on 2009-08-19
in the last few days i've been trying to make the ppa packages a bit less dangerous on install but its still a bit of a gamble :)
on the tty note, theres a few issues with fonts at the moment (some dont exist as named and this can lead to invisible tty's).
 i've replaced all the main fonts here and made sure the themes only use fonts that actually exist, i'll try and upload packages that reflect this in the next couple of days
grub doesnt handle 'loadfont' failing particularly well, hopefully this will default to a backup in the future. just now a few missing loadfont will send grub into a 'missing file' spiral, there seems to be no way out of this apart from rebooting to another bootloader. i might make sure fonts exist by adding a forced update-grub on grub-themes-gfxmenu install just to make sure grub.cfg is coherent
at the moment i've replaced helvetica from x11 fonts and removed New Century Schoolbook since they were a little broken. ive also  added liberation fonts.
in the day or two i'll upload a new addition to grub-custom-scripts that should take a font directory and convert all fonts to a range of sizes from 8 to 24 in a regularly named pf2 file with the format,
<font name>-<style>-<size>.pf2 which should make theming a bit easier.
i'll also try and go through the available themes and make sure they use actual existing fonts, maybe move all themes to 1024x768 for simplicity too. i'll be very glad when gfxmenu moves to non-pixel placement :)

---

### Post by cecilpierce on 2009-08-21
Im only getting "quiet splash" on the first menu listing, I have 4 other ubuntu OS's and its missing.
In /etc/default/grub:GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Do need to do something else or what am I doing wrong ?

---

### Post by dinxter on 2009-08-21
> **cecilpierce said:**
> Im only getting "quiet splash" on the first menu listing, I have 4 other ubuntu OS's and its missing.
In /etc/default/grub:GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Do need to do something else or what am I doing wrong ?
whats your /etc/grub.d/50_grub-custom-scripts look like? the rename_menu function isnt too bright, its just a ugly brute force method of renaming entries, it doesnt like '|' or ' " ' characters, and while renaming to "" will delete a menu, renaming to " " will just rename it to a space. make sure your using the latest version of grub-custom-scripts too, it seems to be the least error prone here so far

---

### Post by cecilpierce on 2009-08-21
50_grub-custom-scrips

#!/bin/bash
. /etc/grub.d/grub-custom-scripts_lib
## Rename or delete a menu entry from /boot/grub/grub.cfg, for example

## This will rename the menu entry to Karmic Koala
#rename_menu "Ubuntu, Linux 2.6.31-5-generic" "Karmic Koala"

## This will delete an entire entry
#rename_menu "Ubuntu, Linux 2.6.31-6-generic"  ""

## Set the background for gfxterm
#set_background "/usr/share/images/grub/BonsaiTridentMaple.tga"


## Enable gfxmenu and set the theme
set_gfxmenu_theme "/boot/grub/themes/ubuntu2/theme.txt"

I changed the theme, the blinking on the other was making me blind !
Thanks,
Cecil

---

### Post by dinxter on 2009-08-21
sorry, i totally misunderstood, i thought you were having a problem with renaming but i see you arent using that. is it just that your other entries are missing "quiet splash"? the gfxmenu script tries to add --class options to menu entries, maybe thats causing a problem. if you turn gfxmenu off and run update-grub to the "quiet splash" options appear ina all your expected entries ok? if so, what are the actual menu entries in /boot/grub/grub.cfg after the update? maybe theres some dodgy pattern matching going on

---

### Post by dinxter on 2009-08-21
sorry, its a friday thing :) but, setting gfxmenu doesnt touch any other lines apart from menuentry lines, so it wont effect "quiet splash" options, they're on the linux line. note, quiet/splash will only be added automatically to grub entries for identified linux kernels, not recovery entries.

---

### Post by cecilpierce on 2009-08-21
Well I disabled gfxmenu and update-grub and the grub.cfg still only has quiet/splash in the one im using right now. I noticed UUID line on this one "linux   /boot/vmlinuz-2.6.31-6-generic root=UUID=558c8ba5-1d86-4d27-b74b
-c76171b1b60c ro   quiet splash" the others say "linux /boot/vmlinuz-2.6.31-6-generic root=/dev/sdb6" Maybe I need to reinstall grub or go on a vacation !
Cec

---

### Post by dinxter on 2009-08-21
> **cecilpierce said:**
> Well I disabled gfxmenu and update-grub and the grub.cfg still only has quiet/splash in the one im using right now. I noticed UUID line on this one "linux   /boot/vmlinuz-2.6.31-6-generic root=UUID=558c8ba5-1d86-4d27-b74b
-c76171b1b60c ro   quiet splash" the others say "linux /boot/vmlinuz-2.6.31-6-generic root=/dev/sdb6" Maybe I need to reinstall grub or go on a vacation !
Cec
i'd probably go for the holiday myself :)
 i'm not sure which would be the best way to fix it. grub-mkconfig and os-prober should really take care of it, maybe someone else knows.
all the same i might add an add_menu_option "menu name" "option" to grub-custom-scripts at some point to allow people to add and remove automatically set options in grub.cfg. for tinkering purposes, or accidentally delete the whole file, who knows...

---

### Post by cecilpierce on 2009-08-21
OK dinxter, thanks, I guess i'll edit it back for now.
Just did dist-upgrade and have more probs with nvidia junk ! See you when I get back from vacation (Mars or maybe Pluto).

---

### Post by cecilpierce on 2009-08-21
Everything is back to 'so called' normal but when is this blinking grub menu going away ? Where or what file(s) should I look at ?

---

### Post by dinxter on 2009-08-23
i've seperated themes into two packages for ease of fiddling
grub-themes-gfxmenu - all the gibibit and arch forum themes
grub-themes-gfxmenu-extra - some other themes which now use the included Liberation fonts, regular or bold in a range of sizes

have done this for ease of fixing, many of the original fonts are wrongly named and regenerating them with grub-mkfont doesnt seem to help. i can try and keep the 'extra' ones working... hopefully.
i've left out grid layed out menus, scrollbars and such out of 'extras' too, until the redraw is fixed it causes painful eye twitching on my computer

---

### Post by dinxter on 2009-08-23
> **cecilpierce said:**
> Everything is back to 'so called' normal but when is this blinking grub menu going away ? Where or what file(s) should I look at ?
i'm not sure what you mean here, you cant have a gfxmenu if you've got the current grub-pc from the repositories installed, are you sure you have the right ones?

---

### Post by cecilpierce on 2009-08-23
Im not sure whats going on, I have been having upgrade problems but I think I have it fixed ???
Anyhow here is what I have for grub2.

---

### Post by dinxter on 2009-08-23
> **cecilpierce said:**
> Im not sure whats going on, I have been having upgrade problems but I think I have it fixed ???
Anyhow here is what I have for grub2.

you still have the ppa versions of grub2 ppa packages installed (note the ~dinxter tag) to force downgrading to proper repository grub

```
sudo apt-get install grub2=1.96+20090725-1ubuntu2 grub-pc=1.96+20090725-1ubuntu2 grub-common=1.96+20090725-1ubuntu2
```if you also want to get rid of the custom scripts and the themes 
```
sudo dpkg --purge grub-custom-scripts grub-themes-gfxmenu grub-themes-gfxmenu-extra 
```note, you may not have all of these theme packages installed at the moment, i cant see in the picture

---

### Post by dinxter on 2009-08-23
also, after doing that you will need to get rid of the ppa from synaptic as it will try to upgrade grub2 to the ppa if you dont. also also :) once you've got rid of everything above you could run update-grub again, it should make sure your grub.cfg is de-gfxmenu'd, although it shouldnt cause any problems if you forget

---

### Post by Totzo on 2009-09-06
just wondering if there will be a gfxmenu version of the new 1.97 beta? Cheers!

---

### Post by dinxter on 2009-09-06
> **Totzo said:**
> just wondering if there will be a gfxmenu version of the new 1.97 beta? Cheers!
theres been a lot of changes in grub2 since the gfxmenu patch which means it would be a bit more work to make it fit with the newer grub, i might do it but the author, colin bennett, is in the process of merging gfxmenu into grub2 trunk which means it will either arrive officially as part of a ubuntu grub2 update or it will be much easier to make a patch for the current grub so i'll probably wait for the merge before giving that a stab

---

### Post by Totzo on 2009-09-06
> **dinxter said:**
> theres been a lot of changes in grub2 since the gfxmenu patch which means it would be a bit more work to make it fit with the newer grub, i might do it but the author, colin bennett, is in the process of merging gfxmenu into grub2 trunk which means it will either arrive officially as part of a ubuntu grub2 update or it will be much easier to make a patch for the current grub so i'll probably wait for the merge before giving that a stab

I wondered if that might be the case- look forward to seeing the outcome.

---

### Post by cecilpierce on 2009-09-11
Anything new with theming? I cant wait.

---

### Post by dinxter on 2009-09-11
> **cecilpierce said:**
> Anything new with theming? I cant wait.
if you mean the gfxmenu stuff then see above
i can't imagine it'll be in karmic but i'll be trying to make a patch once its in svn, hopefully someone will get there before me and post it up here :)

---

### Post by cecilpierce on 2009-09-11
Yea dinxter, gfxmenu, I must have done something wrong, I cant get it to work anymore. Maybe the grub2 beta did it. Oh well I was just wondering if you guys were still tinkering with it and if there was something new.
Thanks, Cec

---

### Post by dinxter on 2009-09-12
> **cecilpierce said:**
> Yea dinxter, gfxmenu, I must have done something wrong, I cant get it to work anymore. Maybe the grub2 beta did it. Oh well I was just wondering if you guys were still tinkering with it and if there was something new.
Thanks, Cec
the last working patch i had was for 1.96+20090725 and now we're on []("https://launchpad.net/%7Edinxter/+archive/experimental/+sourcepub/695690/+listing-archive-extra")1.97~beta2. i had a look at it but it required a bit more rewriting than my effort levels were up to ( ie, beyond superficial changes), since this is already being done by a professional :) unless theres a few rainy weekends i'll just be keeping my eye on svn

---

### Post by dinxter on 2009-09-18
for info and/or playing, the branch for work on merging 
gfxmenu is being done on git below
[http://github.com/bean123/grub/](http://github.com/bean123/grub/)

---

### Post by brandjamie on 2009-10-18
Hi. 
After many scary moments and amazingly no disasters I've got the gfx menu's working. So much thanks to everyone on this thread for that. 
The graphics and menu options are still blinking though (as mentioned by others). Did anyone find a way to stop this?

---

### Post by dinxter on 2009-10-18
the blinking is due to redraw not being optimised yet (fix first, profile last :)) theres been a lot of work done though ( its been a few months since this version ) and i hear the finished version is just about ready for playing with

---

### Post by pxwpxw on 2009-10-19
Some current late stage testing for Apple efi version, with useful results in Apple forum. (frequent updates)
Fancy menu for GRUB EFI (Bean)
[http://ubuntuforums.org/showthread.php?t=1248647](http://ubuntuforums.org/showthread.php?t=1248647)
I don't know if any one has been testing on pc version.

---

### Post by raprap30 on 2009-10-21
Pxwpxw: I tried and it doesnt work XD. I'll try to see if I got any thing wrong. I doubt that it will work on PCs

---

### Post by pxwpxw on 2009-10-21
> **raprap30 said:**
> Pxwpxw: I tried and it doesnt work XD. I'll try to see if I got any thing wrong. I doubt that it will work on PCs

The Apple thread binaries are for EFI boot, which is much easier to install. 
For pc version it needs compile and install grub2 using source from
 [http://github.com/bean123/grub/](http://github.com/bean123/grub/)
and demo scripts from
 [http://grub4dos.sourceforge.net/menu.zip](http://grub4dos.sourceforge.net/menu.zip)
grub-devel thread -
 [http://lists.gnu.org/archive/html/grub-devel/2009-09/msg00286.html](http://lists.gnu.org/archive/html/grub-devel/2009-09/msg00286.html)

---

### Post by ridgeland on 2009-10-21
Thanks Nate B. for posting #66 with the clip from grub.cfg.
I could not get update-grub to populate that section so I edited grub.cfg now I have my splash image.
I did skip the search line though as I've hit snags with that.
Next step is to learn how to edit /etc/grub.d/05... so update-grub will keep my settings.  
I changed /etc/grub.d/30... commenting out everything and changed /etc/grub.d/40 adding the stanzas the way I want them.
Funny thing is after all those tries I reran update-grub with the changes to /etc/grub.d/* and now it does populate section 05 correctly!  I think my difficulty related to set root issues.

---

### Post by raprap30 on 2009-10-21
But how should I do it, and btw have you tried Chameleon 2.0rc?

---

### Post by ranch hand on 2009-10-21
> **raprap30 said:**
> But how should I do it, and btw have you tried Chameleon 2.0rc?
Do what?

---

### Post by raprap30 on 2009-10-22
> **ranch hand said:**
> Do what?

Never Mind... I just hope that gfxmenu will be out with ubuntu with a GUI theme changer soon...

---

### Post by tobarello on 2009-10-23
Hi everybody!
I've added Dinxter PPA and installed grub-pc grub2 grub-themes-gfxmenu grub-themes-gfxmenu-extra and grub-custom-scripts.
I have modified the /etc/grub.d/50_grub-custom-scripts enabling the gfxmenu-theme, but when i go "sudo update-grub" this is what i got:
tobarello@tobarello-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found Debian background: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 8.04.3 LTS (8.04) on /dev/sda6
Grub is not gfxmenu enabled...
done
Anyone can give me some hints?

---

### Post by ranch hand on 2009-10-23
That looks like you have 9.10 installed and running grub2 along with Hardy on sda6.

Is something wrong with that?

[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

There is some basic info there and links to more in depth information.

---

### Post by tobarello on 2009-10-23
Nothing wrong I have ubuntu 8.04 with the -rt kernel on that partition...
the point is that i can't enable gfxmenu on dinxter grub-pc package...

---

### Post by ranch hand on 2009-10-23
Ah, I have a lot of 9.10 installs and have never used that, though I keep threatening to.

I think that the entire /boot/grub/grub.cfg file might be of more help in diagnosis.  I don't know for sure but I think that will give a better view of what is happening.

The only thing that I can think of is - Have you checked to make sure that your script file /etc/grub.d/50_grub-custom-scripts under permisions is checked so that it is executable?  If not that would be your problem.  Fix that and run sudo update-grub again and see what happens.

---

### Post by tobarello on 2009-10-23
thanks for your help ranch hand. But that wasn't the problem.
I'm attaching my grub.cfg. But i think that I could have misunderstood the correct procedure.
Would you mind posting all the steps that I need to take to try out gfxmenu themes in grub2?
Thanks in advance

---

### Post by dinxter on 2009-10-23
The message your getting is the result of 
/boot/grub/gfxmenu.mod
not existing. This means that you probably don't actually have the ppa version of grub-pc installed. Because these are older packages ( I havent been fixing them for a while now ) you might find they have been replaced by newer ones from the main repository.  If the installed version contains ~dinxter in it then you might want to try reinstalling the packages.

---

### Post by tobarello on 2009-10-24
Ok i solved the problem via synaptic...

I had the correct packages installed, but probably because I had an usb pen drive mounted, the first time i installed them, grup-pc was configured to be placed in /dev/sdb instead of /dev/sda.

I debconf grup-pc a second time and that did the trick!
Thanks for your response and for the good work.

I'm really having fun with linux!

---

### Post by ranch hand on 2009-10-24
tobarello
Just to let you know, the reason I wanted to see the grub.cfg file was to see if you had the last entry in it.  You do.  This indicates that the script is  executable.

Now that you have it working (GREAT), if you look at that same file the last entry should be different as it is now functioning.

---

### Post by shawe_ewahs on 2009-10-27
dinxter do you know if grub2 1.97~beta4-1ubuntu3 in oficial repository has gfxmenu included yet? Now I can see your theme ubuntu-karmic in my grub and after only background images, but with another font style different that your screenshot :S.

Can you confirm if this is true please?

I'm modifying your theme ubuntu-karmic, adding more distro logos and creating lines for some distros.

---

### Post by dinxter on 2009-10-28
gfxmenu is not in grub2 in ubuntu, because gfxmenu is not in grub2's own main repository yet! you could try bean123's development branch of grub2 at [https://launchpad.net/burg](https://launchpad.net/burg) but its a development branch so I would only use it on a virtual machine at the moment

---

### Post by shawe_ewahs on 2009-10-28
Why works gfxmenu for me only adding your scripts on /etc/grub.d/ and images, fonts and themes on /boot/grub?

---

### Post by dinxter on 2009-10-28
Either you have a different version of grub2 installed than the official one, such as the one in my ppa (If /boot/grub/gfxmenu.mod exists then you do)
Or you only have the background image installed and menus renamed, which is different than the more advanced gfxmenu stuff.
But as I say, gfxmenu is not in any version of grub2 in ubuntu, and is not even in the grub2 main upstream svn yet

---

### Post by shawe_ewahs on 2009-10-28
dinxter you have reason, I try to put in a virtual machine and it don't work, I'm trying to copy files needed for show gfxmenu in virtual machine.

This is in my real machine [http://shawe.dyndns.org/](http://shawe.dyndns.org/) your ubuntu-karmic gfxmenu theme modified by me. Sorry for poor quality, but I don't have better camera.

---

### Post by dinxter on 2009-10-28
looks good, theres been a number of things done to it since then, redraw has been optimised I believe so no flickering, submenus, password protected entries, themes switching, that kind of thing. hopefully it'll reach grub main soon and so double hopefully the next ubuntu release

---

### Post by shawe_ewahs on 2009-10-28
dinxter I think that now I know what happens.

If people install from your repo and after update to current version in official ubuntu repos, gfxmenu are also working.

Can be this possible? Or only works because gfxmenu are using different files for work? I don't understand why, but this is the reason that I've the latest grub2 1.97~beta4-1ubuntu3 working with gfxmenu.

If this it's correct, can be interesting do a package that only includes dependecies for gfxmenu, not?

---

### Post by dinxter on 2009-10-28
Difficult to know, gfxmenu itself compiles to a module, but there are changes to the video sytem and so on within the grub version in karmic made by the gfxmenu code too, how essential these are i'm not sure, and obviously bits and pieces affected by the original code have changed inside grub main (and karmic) since colin bennetts original code. (This is partly why I didnt update the ppa version)
But bean123's branch is synced to a more recent grub so it might be possible to do a seperate gfxmenu package, I believe there is already a module for another architecture on another thread somewhere. 
I could attempt something now but I still prefer until the whole thing is merged into grub main before messing about with it, its maybe my laziness but its just easier that way :) Of course, someone less lazy could do it before then!

[EDIT] bean123's thread
[http://ubuntuforums.org/showthread.php?t=1248647](http://ubuntuforums.org/showthread.php?t=1248647)

---

### Post by dinxter on 2009-10-28
at least I think they plan to merge it into grub, I havent been watching too intently recently

---

