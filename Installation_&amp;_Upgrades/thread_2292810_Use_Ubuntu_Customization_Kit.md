---
title: "Use Ubuntu Customization Kit"
date: 2015-08-31
forum: Installation &amp; Upgrades
---

### Post by tamir2 on 2015-08-31
Hello, I hope will respond to my question.
I need to make a custom Ubuntu installer for use in rural classrooms. Suitable distro, taking into account local needs, I did not find, so I decided to do it myself :). As an assistant in this case used the UCK. But there are several issues that require solutions:
1)  UCK deploying a system image, at the stage of creating the profile  chroot at /home/user/tmp/remaster-root/home/[user], which is  called the name of your profile which makes assembly of the  distro. That  is, if you make a distro to the OS under the profile of "John"  then the script will create a similar profile in the deployed system. This (my) profile then is packed with all the guts in the system image. The question of how to eliminate the profile folder, not to break the build process? Can fix this by editing the scripts USC? What and where to register?
2) How to increase the degree of compression wrapping system UCK? It may also change the script? How and where?

---

### Post by tamir2 on 2015-09-01
Can anyone help with a change script to rebuild Xubuntu 14.04?
/script attach/

---

