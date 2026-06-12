---
title: "Adobe reader installation..problem"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by johnjude on 2005-11-28
I have downloaded latest version from adobe website as .rpm package.Then i converted it to .deb and installed.
Now,If open any pdf file using that,the error message "could not find acroread exec file" is coming..please anyone to help me....

---

### Post by David Haas on 2005-11-28
johnjude--I installed Adobe Reader the other day from the Ubuntu repository. You don't want to download and try to install an rpm package into a Debian-type distribution, if you have better options. Do it through Synaptic Package Manager. Get into Synaptic (System>Administration>Synaptic Package Manager) and open the listing of Repositories (Settings>Repositories). Then add, if not already added, all the repositories, including the ones marked Universe and Multiverse. Then, do a "Reload" from the top taskbar--this will update the packages in your repositories. Then, go to the package marked acroread--packages are listed alphabetically. Mark it for installation and then click "Apply" at the taskbar. That's it. The package and its dependencies will be installed. Then you just need to select the icon for it, if you like--but this is another (minor) matter.
Good luck,
David

---

### Post by arphe_el on 2005-11-28
I want adobe acrobat to plugin to firefox browser i already follow the command in ubuntu starter guide for installing it such

sudo apt-get install mozilla-acroread
sudo apt-get install acroread-plugins

also I already i already updated my sources.list repositiories also i already performed after editing the list sudo apt-get update still there is an error message like this as i install mozilla-acroread and acroread-plugins. What seems to be the problem? any advice

here are the output after i enter the above commands:
E: Couldn't find package mozilla-acroread
E: Couldn't find package acroread-plugins

Thank you and GODspeed!

---

### Post by David Haas on 2005-11-29
arphe_el---I recommend installing using Synaptic Package Manager by the steps I specified before. When you use the shell instead of Synaptic, you must type in the correct name of the packages, of course. My recollection is that "mozilla-acroread" is incorrect. I believe I installed Adobe Reader months ago by typing "install acroread." After acroread is installed, I think that you can select it in preference to xpdf as the default PDF application for opening PDF files at the browser--this would be done in a dialogue box, I recall.
David.

---

