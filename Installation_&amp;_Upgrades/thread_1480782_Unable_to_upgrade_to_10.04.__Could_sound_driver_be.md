---
title: "Unable to upgrade to 10.04.  Could sound driver be the issue?"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by CompSciSTL on 2010-05-11
I'm currently trying to upgrade to 10.04, but I'm experiencing a problem. Currently I am encountering the following error message when trying to upgrade:

"An unresolvable problem occurred while calculating the upgrade: The package 'ubuntu-desktop' is marked for removal but it is in the removal blacklist."

The message directed me to /var/log/dist-upgrade. I looked at the apt.log file and I discovered the following at the end of the file:

"Investigating ubuntu-desktop
Package ubuntu-desktop has broken Depends on libsdl1.2debian-pulseaudio
Considering libsdl1.2debian-pulseaudio 2 as a solution to ubuntu-desktop 0
Re-Instated libsdl1.2debian-pulseaudio
Re-Instated ubuntu-desktop
Investigating libsdl1.2debian-alsa
Package libsdl1.2debian-alsa has broken Conflicts on libsdl1.2debian-pulseaudio
Considering libsdl1.2debian-pulseaudio 2 as a solution to libsdl1.2debian-alsa 10
Added libsdl1.2debian-pulseaudio to the remove list
Fixing libsdl1.2debian-alsa via keep of libsdl1.2debian-pulseaudio
Investigating ubuntu-desktop
Package ubuntu-desktop has broken Depends on libsdl1.2debian-pulseaudio
Considering libsdl1.2debian-pulseaudio 2 as a solution to ubuntu-desktop 0
Removing ubuntu-desktop rather than change libsdl1.2debian-pulseaudio"

Could there be some sort of issue with the sound driver(s) which is preventing the upgrade?  :confused:

---

### Post by CompSciSTL on 2010-05-16
Does anyone have any idea why this is happening?  :-k

---

### Post by mistichu on 2010-05-16
download all updates for current distro (note you will be unable to upgrade from say feisty because of depends) currently as far as i know you must have jaunty(9.04) or karmic(9.10) to upgrade so download all updates for distro then upgrade it should fix any broken dependicies you have (which is why you cant upgrade )

EDIT:
see when you upgrade you retain all of your programs and most of your settings so if you had a dock or a widget on your desktop then it would be there when you upgraded so if you had something that had major changes to critical files you would need to update all of your packages inorder to upgrade :)

also it appears that you have pulse and alsa installed which depending on your configuration may cause conflicts

---

