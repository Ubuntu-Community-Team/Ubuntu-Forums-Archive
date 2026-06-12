---
title: "Install  Xubuntu 7.04 Feisty Fawn Server"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by Diana Rogger on 2007-06-20
Hi,

I am new on this forum.
I had Fedora1 installed on my computer but later I installed Fedora6 but I have had problems with Fedora6. If you don't have Internet you cannot see what software is installed on your computer. 

So I want to try Xubuntu. 
I downloaded Xubuntu 7.04(Feisty Fawn) and installed it.
So I have some quwstions:

1) Is it posible to download the rpm files, burn them on a cd to install them to an other computer?

I want to put the rpm files on a cd to install them at home because I do not have Internet yet.

2) How can I install a rmp file if I allready put it on a cd?

Thank you in advanced.

Regards,

Diana Rogger

---

### Post by stalker145 on 2007-06-20
Welcome to the forum.

When you talk about downloading rpm's and burning them, I assume that you are talking of software outside the initial install that you'd like to put on your machine?

If this is accurate, it *is* possible to do that. The main thing is that Ubuntu and its derivatives use deb files vice rpm. The concept is the same. The only problem that you would possibly run into is if the deb that you are trying to install has dependencies that are not already on your internet-less machine. In that case, you would have to make sure to download all of them as well. It's sometimes a convoluted pain in the rear if you don't have internet access with Linux.

Basically, make sure that any debs that you get have all the files within them that you need to install whichever program you're going for and you'll be golden.

Now, with all of this said, it is possible to install rpm files as well, but it requires installation of more software and then a few keystrokes that I haven't taken the time to learn as of yet.

Good luck with this. Check back if you need more.

---

### Post by Diana Rogger on 2007-06-20
Hi,

Thanks for your reply.
So it is posible if I put all the deb files on a cd or a dvd.

Question:

1) What command must I use to install a deb file from a cd?
2) Or do I have to copy them first in a folder on the computer?

Which steps I have to take?

Thank you in advanced.

Regards,

Diana

---

### Post by stalker145 on 2007-06-20
The way I usually install debs is to simply double-click them. There is also the terminal option:```
sudo dpkg -i package_name.deb
```

Someone please correct me if my code is wrong since I don't think that I've *ever* used that route.

You should be able to install directly from the CD either from the terminal or from your file manager. Just remember that you *might* end up needing some extra files once you get around to installing. Those are the dependencies that I spoke of before. Just make sure to check what your desired application requires (depends upon) for install, grab those, and you'll be fine.

---

### Post by Diana Rogger on 2007-06-21
Thank you for your support.

Regards,

Diana

---

