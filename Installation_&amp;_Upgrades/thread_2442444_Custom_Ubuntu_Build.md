---
title: "Custom Ubuntu Build"
date: 2020-05-03
forum: Installation &amp; Upgrades
---

### Post by obsidiangroup on 2020-05-03
Greetings,

I am looking for a way to build a custom Ubuntu image/installer.  I know there are tools like Cubic, etc.  But these tools, from reading the documentation, do not support what we are attempting to do.

We are looking to create a custom Ubuntu image/installer, but during the installation process the installer would prompt the user to answer questions / pick certain software to be installed, etc.

I have not found a way (or just have missed it) to create a custom Ubuntu image with a custom installer, or a way to edit the ubuntu installer.  We want to be able to present the user with something like:

Select which services you would like to install.
=============================
1) Software Package A
2) Software Package B
3) Software Package C

and if user selects option 2, then they are presented with another menu:

Software Package B Installation Options
=========================
1) Enter Default Port to run on (Default: 2601): _____
2) Enter Administration Username (Default: admin): _______
3) Enter Default Password (Default: <no password>): ________

Then the installer would return to the previous menu to give the user options to continue installing software.  Once the user has finished selecting the options, the installer would then run the various installation scripts while installing Ubuntu.

Thanks in advance for any pointers.

---

### Post by oldfred on 2020-05-03
Neither of these are exactly what you want.

Used by Server install to choose what you want
sudo apt install tasksel

Not sure this is still available.
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

Why not do a standard install, then run a script to add the options.
I do that will all my installs, but do not ask questions.

---

### Post by obsidiangroup on 2020-05-05
We are creating an installation that other users outside of our organization may use, so having the user run a script once the install defeats that purpose. We want the installation, once complete, to be ready for the user to use. We have considered using a web-based setup but thinking some sort of way of a custom install script that prompts for certain configurations then once the system is installed the user could go to a webpage to finish setup, but really would rather modifying the Ubuntu installer so everything can be done during initial install.

---

