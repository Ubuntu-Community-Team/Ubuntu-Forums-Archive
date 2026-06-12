---
title: "boot from cd with persistence"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by phvrc2nt on 2009-12-11
is it possible to always boot ubuntu using a dvd-rom while also having it to accept new software installation and data save?

this is my scenario.

i need to boot ubuntu thru cd-rom
install software.
save files.

without it altering my hard drive.
but instead doing it on a usb drive?

/// not an option booting a usb persistent drive ///

thanks for the help.

---

### Post by raymondh on 2009-12-11
> **phvrc2nt said:**
> is it possible to always boot ubuntu using a dvd-rom while also having it to accept new software installation and data save?

this is my scenario.

i need to boot ubuntu thru cd-rom
install software.
save files.

without it altering my hard drive.
but instead doing it on a usb drive?

/// not an option booting a usb persistent drive ///

thanks for the help.

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

Better yet, this paragraph from the above-link...

[I]**Booting the Live CD in Persistent Mode**

Now we get to enjoy the fruits of our labor. Make sure your USB Stick is plugged into your computer and take the Live CD that you downloaded and burned earlier and put it in your CD drive (if it is not already there). Reboot your computer and boot up using this Live CD.

Before you reboot there are only two things that you need to remember. When the Live CD menu gets displayed hit the <F6> key to enter “Other Options”. This will display the arguments that the Live CD passes to the kernel. At the end of this argument list just add a space and add the word “persistent”. This will instruct the Live CD to maintain and use persistence. That is all. Go for it!

Note: It appears that with Flight 5, you need to create a new user in the Live CD session (go System -> Administration -> Users + Groups, then press the "Add User" button) for it to save your settings; it does not appear to save most changes to the default user, "ubuntu". When you create the new user, be sure to check the box in the "user privileges" tab that says "executing system administration tasks" or you'll be pretty limited in what you can do :)

When you get back, or better yet, when you boot into your live environment come back to this page and see how you perform a few basic tests to make sure everything is working correctly. [/I]

I've never tried it.  Post back results as it would be an interesting project to make for friends.

Happy ubuntu-ing :)

---

### Post by raymondh on 2009-12-11
Reading further ... seems to me that you need a persistent USB to make the liveCD persistent as well.  Sorry.  Now that this caught my interest, 'will research further.

regards,

---

