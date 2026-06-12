---
title: "Xubuntu 7.04 to Ubuntu 7.10"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by sargonious on 2007-10-05
I currently have Xubuntu 7.04 installed on my 533 MHz IBM 300PL with 384 megs of RAM. Here's a list of what I want to do.

I'm installing a 256 MB video card with DVI output...

I'm switching to a 19 inch LCD Widescreen Montior...

When Ubuntu 7.10 comes out I want to install that and not Xubuntu.

What do I need to do? I have tried switching monitors before but Xubuntu doesn't seem to be plug n play. Do I need to configure the XORG.config file? How do I switch to Ubuntu when I upgrade to 7.10?

---

### Post by Ub1476 on 2007-10-05
I guess the easiest way is to make a backup of your files and do a clean install, so Ubuntu will detect your hardware, and configure it automatically. A clean install is always recomended anyway:)

---

### Post by MadMarv on 2007-10-05
To get your new monitor or video card recognized by Xubuntu - or any 'buntu, for that matter - you can type the follow command in your terminal:

sudo dpkg-reconfigure xserver-xorg

This starts the same xserver setup you do at install. Just to be on the safe side, I would backup your xorg.conf file first so you can go back to your original hardware if things don't work.

As for upgrading and changing to Ubuntu without starting from scratch, I would change to Ubuntu first by installing ubuntu-desktop from the repositories, and upgrading after. This leaves Xubuntu available as an option in your session startup menu. If you want to remove it later, I seem to remember posts explaining how to do it. I'd leave it, though. Always a good idea to have a backup session available.

---

