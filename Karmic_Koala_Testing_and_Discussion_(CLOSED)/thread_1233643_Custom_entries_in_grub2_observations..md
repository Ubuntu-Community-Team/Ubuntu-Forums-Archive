---
title: "Custom entries in grub2 observations."
date: 2009-08-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-08-06
I have 10 OS' on my external drive.  I wanted labels.  So I learned to do the custom entry in grub2.  This is very cool.  I love it.

My most recent additions are both Mandriva.  It is a little tricky to get to boot anyway and is easiest in a custom entry.

The problem is that on running update grub, where they showed up on the terminal, they did not turn up on the menu generated in grub.cfg.  WTF?

So I played abit and found that if I put them anywhere in the 04_custom file, except the end, they showed up.  The reason I tried that is because I thought maybe there was a limit to the number of custom entries.

There does not seem to be a limit.  There does seem to be some reason that thes 2 will not show up unless there is an OS after them.  I am on the idea that grub2 just doesn't "like" none Debian based OS' right now.  I may haveto try something else to see.

---

### Post by drs305 on 2009-08-06
Do you know if the same thing happens if you have them in 40_custom instead of 04_custom? I was just wondering if there may be something about them showing up before the 10_linux entries. I wouldn't think so...

---

### Post by ranch hand on 2009-08-06
That is an excelant question.  I will give it a whack tommorow.

Right now there are 4 versions of 9.10 ahead of them and 8.04 and 3 versions of 9.04 after them.

I just cut/pasted one of the 9.04s to a spot after 1 of the Mandrivas and before the other Mandriva.  The 1 left at the end did not show up, the one with 9.04 after it did.  It was then that I just cut/pasted both Mandrivas to the middle of the list.

Now all 10 show up fine.

I like to have the 9.10 I am booting from to be first and the other 9.10s right after it so that I can do the daily update starting at the bottom of the 9.10 list and work up and do the one that needs to be updated to find them all last so that I can work on any problems and not risk having to do it again after updating something else.

I have also though of having more than one custom file so that you only edit the one that has the most volitile OS'.

I think that grub2 is going to be absolutely great when it has been "smoothed" a little bit.

---

### Post by ranch hand on 2009-08-07
Well, now I am truely confused but happy about it.

My custom file was 04_custom.  I did a number of things to it.  First cut the Mandriva entries and pasted them to 40_custom;
```

04_custom (- Man) and 40_custom

jak@jak-desktop:~$ sudo update-grub 
Generating grub.cfg ... 
Adding KinkyStoner1.0 on sda12 
Adding KinkyStonerA2 on sda8 
Adding Kinky-Grub2-A2 on sda10 
Adding KinkyA3 on sda13 
Adding MAIN on sda6 
Adding SuperOS on sda7 
Adding JauntyVB on sda9 
Adding Stoner1.1 on sda11 
Found Debian background: NICE.png 
Found linux image: /boot/vmlinuz-2.6.31-5-generic 
Found initrd image: /boot/initrd.img-2.6.31-5-generic 
Found memtest86+ image: /boot/memtest86+.bin 
Found Ubuntu karmic (development branch) (9.10) on /dev/sda10 
Found Ubuntu 9.04 (9.04) on /dev/sda11 
Found Ubuntu karmic (development branch) (9.10) on /dev/sda13 
Found Mandriva Linux 2009.1 (2009.1) on /dev/sda14 
Found Mandriva Linux 2009.1 (2009.1) on /dev/sda15 
Found Ubuntu 8.04.3 LTS (8.04) on /dev/sda6 
Found Ubuntu 9.04 (9.04) on /dev/sda7 
Found Ubuntu karmic (development branch) (9.10) on /dev/sda8 
Found Ubuntu 9.04 (9.04) on /dev/sda9 
Adding Man-Gnome on sda14 
Adding Man-Both on sda15 
done 
jak@jak-desktop:~$

```
This worked very well but puts the Man entries at the end of the boot menu.

Then created 06_custom and just copied 40_custom to it;
```

04_custom – Man and 06_custom and 40_custom

jak@jak-desktop:~$ sudo update-grub 
Generating grub.cfg ... 
Adding KinkyStoner1.0 on sda12 
Adding KinkyStonerA2 on sda8 
Adding Kinky-Grub2-A2 on sda10 
Adding KinkyA3 on sda13 
Adding MAIN on sda6 
Adding SuperOS on sda7 
Adding JauntyVB on sda9 
Adding Stoner1.1 on sda11 
Found Debian background: NICE.png 
Adding Man-Gnome on sda14 
Adding Man-Both on sda15 
Found linux image: /boot/vmlinuz-2.6.31-5-generic 
Found initrd image: /boot/initrd.img-2.6.31-5-generic 
Found memtest86+ image: /boot/memtest86+.bin 
Found Ubuntu karmic (development branch) (9.10) on /dev/sda10 
Found Ubuntu 9.04 (9.04) on /dev/sda11 
Found Ubuntu karmic (development branch) (9.10) on /dev/sda13 
Found Mandriva Linux 2009.1 (2009.1) on /dev/sda14 
Found Mandriva Linux 2009.1 (2009.1) on /dev/sda15 
Found Ubuntu 8.04.3 LTS (8.04) on /dev/sda6 
Found Ubuntu 9.04 (9.04) on /dev/sda7 
Found Ubuntu karmic (development branch) (9.10) on /dev/sda8 
Found Ubuntu 9.04 (9.04) on /dev/sda9 
Adding Man-Gnome on sda14 
Adding Man-Both on sda15 
done 
jak@jak-desktop:~$

```
This also worked well.

Then I wondered if a setup like I had when the Man entries wouldn't show up on the menu would work if they were in 40_custom so I created 03_custom and moved the 04 and 06_custom files to a new holding directory within /etc.  Tried that;
```

03_custom and 40-custom

jak@jak-desktop:~$ sudo update-grub 
Generating grub.cfg ... 
Adding KinkyStoner1.0 on sda12 
Adding KinkyStonerA2 on sda8 
Adding Kinky-Grub2-A2 on sda10 
Adding KinkyA3 on sda13 
Adding MAIN on sda6 
Adding SuperOS on sda7 
Adding JauntyVB on sda9 
Adding Stoner1.1 on sda11 
Adding Man-Gnome on sda14 
Adding Man-Both on sda15 
Found Debian background: NICE.png 
Found linux image: /boot/vmlinuz-2.6.31-5-generic 
Found initrd image: /boot/initrd.img-2.6.31-5-generic 
Found memtest86+ image: /boot/memtest86+.bin 
Found Ubuntu karmic (development branch) (9.10) on /dev/sda10 
Found Ubuntu 9.04 (9.04) on /dev/sda11 
Found Ubuntu karmic (development branch) (9.10) on /dev/sda13 
Found Mandriva Linux 2009.1 (2009.1) on /dev/sda14 
Found Mandriva Linux 2009.1 (2009.1) on /dev/sda15 
Found Ubuntu 8.04.3 LTS (8.04) on /dev/sda6 
Found Ubuntu 9.04 (9.04) on /dev/sda7 
Found Ubuntu karmic (development branch) (9.10) on /dev/sda8 
Found Ubuntu 9.04 (9.04) on /dev/sda9 
Adding Man-Gnome on sda14 
Adding Man-Both on sda15 
done 
jak@jak-desktop:~$

```
Worked great.

The problem comes in when I tried 03_custom by it self.  This should have reproduced the original condition of no Man entries showing up in the actual boot menu.  they showed up fine in the update-grub stuff in terminal, just like the old file did.

Then they had the affrontary to show up in the boot menu.  Beats me all together.  I do not believe that there was a problem with the original file as all others have been created by cut or copy/paste (I type slow).

I have another (07_custom) that I am going to try.  It is just like 03-custom but will be after the 05_debian_theme.  I doubt that it makes any difference in the speed of getting to the boot menu but I think I will give it a whack seeing that I already have it sitting there.  I was going to use it next to see if it would work after 03_custom failed to get the Man entries into the menu.

So, I have no idea what caused this in the first place.

On the other hand, I have found that you can really get down to serious playing with grub2 and not break it (I screwed up and had several "custom" files on and they all came up).

While it is still having problems getting usable boot information on some distros the sucker works.

---

### Post by phenest on 2009-08-07
This is looks very complicated. Can I just clarify a few things with you just in case you've missed something.
[LIST=1]
[*]Each script is executed in order: 00 01 05 10 20 30 40 etc
[*]Each script can be 'switched on and off'. Setting a script to be executable switches it on (chmod u+x)
[*]And each script that is executed creates a 'graphical layer'
[/LIST]
I'm sure you're familiar with the first two, and I don't want to teach you to suck eggs here. But are you aware of the 3rd? I'll give an example: If you wanted a background image, but that script is performed *after* the menu, the menu is likely to not appear, because the image is drawn over the top. I'll give you my experience of this: I wanted a hidden menu. I found a script and placed it at 04_hidden_menu whcih gave me a nice little countdown "Press ESC for menu... 5". But, because this was before 05_debian_theme (which provided the background), that countdown never appeared, although it was performed.

Do you get my drift here? Simply switch of any of the default scripts you don't need, and place your custom script at 40_custom. But you might also want to break that down into smaller scripts, i.e. 41_custom, 42_custom, and place them in an order that you'd like to see them in the menu.

Also, could you post the contents of your custom file, please?

---

### Post by ranch hand on 2009-08-07
> **phenest said:**
> This is looks very complicated. Can I just clarify a few things with you just in case you've missed something.
[LIST=1]
[*]Each script is executed in order: 00 01 05 10 20 30 40 etc
[*]Each script can be 'switched on and off'. Setting a script to be executable switches it on (chmod u+x)
[*]And each script that is executed creates a 'graphical layer'
[/LIST]
I'm sure you're familiar with the first two, and I don't want to teach you to suck eggs here. But are you aware of the 3rd? I'll give an example: If you wanted a background image, but that script is performed *after* the menu, the menu is likely to not appear, because the image is drawn over the top. I'll give you my experience of this: I wanted a hidden menu. I found a script and placed it at 04_hidden_menu whcih gave me a nice little countdown "Press ESC for menu... 5". But, because this was before 05_debian_theme (which provided the background), that countdown never appeared, although it was performed.

Do you get my drift here? Simply switch of any of the default scripts you don't need, and place your custom script at 40_custom. But you might also want to break that down into smaller scripts, i.e. 41_custom, 42_custom, and place them in an order that you'd like to see them in the menu.

Also, could you post the contents of your custom file, please?
I find #3 very interesting.  I am very new at Ubuntu and Linux in general and a lot of the time I am just running on my gut feelings.  I have been uncomfortable with those files "south" of "05" and that I why I want to go to "06 thru 09".

Putting your custom files in "40" puts them at the end of your menu list while numbers under "10" puts them at the top.  I like them at the top although hitting the "end" key is not hard.

My 03_custom file;
```

#!/bin/sh 
# This file is an example on how to add custom entries 

echo "Adding KinkyStoner1.0 on sda12" >&2 
cat << EOF 
menuentry "KinkyStoner1.0 2.6.31-5-generic" {
	set root=(hd0,12)
	search --no-floppy --fs-uuid --set 2ee327b4-ea23-462e-9c85-9dfcb3b5617d
	linux	/boot/vmlinuz-2.6.31-5-generic root=UUID=2ee327b4-ea23-462e-9c85-9dfcb3b5617d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-5-generic
}
EOF

echo "Adding KinkyStonerA2 on sda8" >&2 
cat << EOF 
menuentry "KinkyStonerA2 2.6.31-5-generic (on /dev/sda8)" {
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 3e5c2219-c1d2-4bb8-ac5c-47a95201876b
	linux /boot/vmlinuz-2.6.31-5-generic root=UUID=3e5c2219-c1d2-4bb8-ac5c-47a95201876b ro quiet splash
	initrd /boot/initrd.img-2.6.31-5-generic
}
EOF

echo "Adding Kinky-Grub2-A2 on sda10" >&2 
cat << EOF
menuentry "Kinky-Grub2-A2 2.6.31-5-generic (on /dev/sda10)" {
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 8a59ea24-d06a-45ce-bd11-665efb66be2b
	linux /boot/vmlinuz-2.6.31-5-generic root=UUID=8a59ea24-d06a-45ce-bd11-665efb66be2b ro quiet splash
	initrd /boot/initrd.img-2.6.31-5-generic
}
EOF

echo "Adding KinkyA3 on sda13" >&2 
cat << EOF
menuentry "KinkyA3 2.6.31-5-generic (on /dev/sda13)" {
	set root=(hd0,13)
	search --no-floppy --fs-uuid --set 291d5f24-4ce9-4125-953f-3d1f52376948
	linux /boot/vmlinuz-2.6.31-5-generic root=UUID=291d5f24-4ce9-4125-953f-3d1f52376948 ro quiet splash
	initrd /boot/initrd.img-2.6.31-5-generic
}
EOF

echo "Adding MAIN on sda6" >&2 
cat << EOF
menuentry "MAIN, LTS, kernel 2.6.24-24-generic (on /dev/sda6)" {
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e2e3cd65-bc09-487f-be96-a83fcc282e38
	linux /boot/vmlinuz-2.6.24-24-generic root=UUID=e2e3cd65-bc09-487f-be96-a83fcc282e38 ro quiet vga=773
	initrd /boot/initrd.img-2.6.24-24-generic
}
EOF

echo "Adding SuperOS on sda7" >&2 
cat << EOF
menuentry "SuperOS, kernel 2.6.28-14-generic (on /dev/sda7)" {
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 30ed6b6a-7eb8-4ef6-b242-c1e19a58d308
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=30ed6b6a-7eb8-4ef6-b242-c1e19a58d308 ro quiet splash
	initrd /boot/initrd.img-2.6.28-14-generic
}
EOF


echo "Adding JauntyVB on sda9" >&2 
cat << EOF
menuentry "JauntyVB, kernel 2.6.28-14-generic (on /dev/sda9)" {
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set f6420b83-12e4-4760-9a79-4fcde04eb797
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=f6420b83-12e4-4760-9a79-4fcde04eb797 ro quiet splash
	initrd /boot/initrd.img-2.6.28-14-generic
}
EOF

echo "Adding Stoner1.1 on sda11" >&2 
cat << EOF
menuentry "Stoner1.1, kernel 2.6.28-14-generic (on /dev/sda11)" {
	set root=(hd0,11)
	search --no-floppy --fs-uuid --set b2279de6-cdfd-4516-9ceb-f083533f83ce
	linux /boot/vmlinuz-2.6.28-14-generic root=UUID=b2279de6-cdfd-4516-9ceb-f083533f83ce ro quiet splash
	initrd /boot/initrd.img-2.6.28-14-generic
}
EOF

echo "Adding Man-Gnome on sda14" >&2 
cat << EOF
menuentry " Man-Gnome on sda14(on /dev/sda14)" {
	linux (hd0,14)/boot/vmlinuz
        initrd (hd0,14)/boot/initrd.img
}
EOF

echo "Adding Man-Both on sda15" >&2 
cat << EOF
menuentry " Man-Both on sda15(on /dev/sda15)" {
	linux (hd0,15)/boot/vmlinuz
        initrd (hd0,15)/boot/initrd.img
}
EOF

```
I suspect that a lot could be edited out of that but I don't really know which stuff so I will leave it for now.  It works very well.

---

### Post by phenest on 2009-08-07
> **ranch hand said:**
> I find #3 very interesting.  

Putting your custom files in "40" puts them at the end of your menu list while numbers under "10" puts them at the top.  I like them at the top although hitting the "end" key is not hard.

I noticed your background was added in between OS's. Thought I'd mention that.

The file numbering doesn't really matter for adding OS's but making sure they're *after* certain other files, such as 05_debian_theme, is something you need to be careful of.

What resolution are you using for Grub? I would have thought a list that long would disappear off the bottom of the screen.:o

---

### Post by ranch hand on 2009-08-07
Yes, the reason forthe theme being picked up there is because the custom file is before the theme file.  I am going to change that when I update tomorrow.

I should explain that kinky kitten is 9.10 and stoner is Stoner Edition1.0, a very nice 9.04 variation.  It has a bunch of addons and I have been upgrading it to kinky on each apha release along with a clean install of each alpha.  Ithink that A4-32 will be a clean install and Stoner-64 will be upgraded.

There has been some problem with the one I am using for my default boot.  No other grub2 will get it right so I think I will just use those 2 partitions, install Stoner again and upgrade it to A4.

A4-32 will have a new set of partitions on my 32bit drive.

---

