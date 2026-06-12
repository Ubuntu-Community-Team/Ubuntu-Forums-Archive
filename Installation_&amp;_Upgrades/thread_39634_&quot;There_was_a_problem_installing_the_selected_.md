---
title: "&quot;There was a problem installing the selected software&quot;"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by thechris on 2005-06-05
"there was a problem installing the selected software

one or more packages failed to install.  this may be due to bugs in the packages, or you may be out of disk space or experiencing some other problem...

Simply trying to install those packages (or a slightly different set of packages) again this may work around the problme or at least move the installation process along a little further.  You will now enter the aptitude, a package management frontend which will give you the opertunity to do this.

it you decide not to try again, bear in mind that some packages on your system will be in a btokern state until you manually resolve the problem"

--what pacakges?  the list of "one or more" is not very helpful.  all i know is that gdm and X do not start after i blindly press g for "get" in aptitude.

---

### Post by mingus on 2005-06-06
Where did you point the installer to get its stage 2 packages to complete the install?  The CD or over the network?  And if the latter, were you actually connected at the time?

I had one install mess up because I missed this detail, said network, but had not yet configured the wireless.  Aptitude is sorta a text-mode gui substitute for Synaptic or using apt-get commands.  Because that was my first Ubuntu install, it was easiest to just reinstall and point to the CD.

Hope this helps.

---

