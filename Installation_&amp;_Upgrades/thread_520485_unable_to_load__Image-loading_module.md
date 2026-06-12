---
title: "unable to load  Image-loading module"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by Mr Happy on 2007-08-08
System: Asus A7n8X, 2.5G Athlon
three partitions: Win2k prof, Ubuntu dapper, Ubuntu Feisty

I upgraded dapper using means I cannot fully recall, following advice from a search.
I added to my sources.list
The upgrade got me to feisty but on the screens instead of text by the side of an icon I had small rectangles for each letter and the same for the emails except the pictures. The browser worked and the open office.

The problem was that nautilus data was not installed and on apt-get upgrade/update I got error messages when it tried to install nautilus data.


I then did apt-get dist-upgrade and about 200MB was downloaded. On restart I saw words and thought this is good.
But the std login did not come up and I got the following error message in a small menu box:

#Unable to load image-loading module
#/usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so:
#/usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so
#Cannot open shared object file: No such file or directory.

I clicked on Ok

then got anther menu box with the following: 

#there was an error loading the theme and the default theme could not be loaded. #Attempting to start the standard greeter.

Click on ok

Then I get a gnome login manager screen, not the normal one. This one has menus that drop down, but I cannot type into the login box.

Pressing ctrl-alt-backspace repeats the above cycle. 

IE if I could kill the x-server then run some upgrades or at least get into the sys.

Any ideas?

---

### Post by ifeldt on 2007-08-08
Have you tried pressing ctrl-alt-F1 at the login screen? This should get you to a terminal where you can login and begin diagnosing your problem.

For me personally, I would backup and data I need to another machine/storage location, and reinstall Feisty.

Have you looked into having a separate partition for your /home? I highly recommend this, as it can save you a lot of trouble down the road. You have to be careful and make sure / and /home are big enough though, as resizing can be slightly painful and have the remotest posibility of hosing the partitions.

---

### Post by pizzipie on 2007-09-03
Mr. Happy,  have you fixed the problem yet? I have the exact same thing happening as I try to update to Edgy. I haven't a clue what to do and updating is a real hassel for me due to satellite internet (slow slow). Any help would be greatly appreciated.

pizzipie

---

