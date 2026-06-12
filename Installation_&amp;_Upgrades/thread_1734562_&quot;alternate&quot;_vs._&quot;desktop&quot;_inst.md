---
title: "&quot;alternate&quot; vs. &quot;desktop&quot; install"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2011-04-20
I must use the "alternate" download for one of my workstations.
The "desktop" download fails with errors (lots of posts about these)
My question is this:

Once I complete the "alternate" install, what packages do I need
(is there a howto?) so that my workstation has identical parts with
the "desktop" install?

I know about **ubuntu-desktop** but are there others?

Thanks in advance,
~~~ 0;-Dan

---

### Post by mikewhatever on 2011-04-20
Nope. Ubuntu-desktop should install all the desktop packages. The real difference is the text based installer, and the final result.

---

### Post by Herman on 2011-04-20
Yes, I agree with mikewhatever.

The main difference is only that the 'Alternate' installation CD itself doesn't boot to a desktop. 

The 'Alternate' installation process uses  simpler graphics, it's more  of a text mode install. 
It has menus for selecting your options and you  need to use your keyboard instead of your mouse.

With the 'Desktop' Live/Install CD people can boot to a Desktop and try  Ubuntu out to before they decide whether they want to install it or not. 
In earlier versions of Ubuntu, the 'Desktop' installer was a little easier for new users to understand, (without needing a guide), but it's debatable whether or not that's still true in recent versions. It does have very nice graphics.

Unless there have been recent changes that I'm not yet aware of,  the  end results from using the 'Desktop' installation CD and 'Alternate'  installation CD are exactly the same.

That is if you only choose to install the  regular operating system.
With the 'Alternate' installation CD, you're not restricted to just the plain ordinary operating system. 
The 'Alternate' CD can optionally be used for making special kinds of Ubuntu installations and includes the ability to:

    * install Ubuntu in a LUKS fully encrypted file system,
    * set up Ubuntu with LVM or software RAID,
    * perform an 'expert' install (for coping with machines with difficult hardware),
    * install ubuntu as a server, (without any desktop (no 'GUI')),
    * the 'Alternate' CD's partitioner will work in a computer with 128 mb of memory and maybe less.
    * choose between GRUB and LILO boot loaders, or even install with no boot loader at all,
    * create pre-configured OEM systems,
    * set up automated deployments,
    * upgrade an older installation without network access.

And also the 'Alternate' installations CD has a 'Rescue Mode', which you can choose when the CD is booting and perform repair and maintenance on the installed operating system if you ever need to.

My first sig link leads to a page which contains further links giving illustrated examples of the 'Alternate' installation CD is use.

---

