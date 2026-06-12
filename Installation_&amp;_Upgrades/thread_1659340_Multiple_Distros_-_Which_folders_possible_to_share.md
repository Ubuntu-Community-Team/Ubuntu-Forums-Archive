---
title: "Multiple Distros - Which folders possible to share"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by wiseguy12851 on 2011-01-03
[LEFT]I'm thinking about installing several distros, but the actual number depends on which folders I can share since I don't want to run into space issues.

Here are the folders / partition's I'm interested in sharing between distros:
    swap
    /boot
    /tmp
    /usr
    /var
    /opt
    /home

Now I know for sure I can share swap and tmp folders, I've read mixed reviews about sharing the actual home folder. Most people say it will work but some advise against it.

I've read only a couple of reviews saying it's okay to share the /boot directory, but personally that sounds like a highly sensitive area of the distro to freely share between distros.

Every review I've read has advised not to think about the /usr directory, I don't understand - if you can share the home folder which contains program configurations
why can't you share the /usr folder itself which contains several of the actual programs.

The others are /var and /opt, I believe I can share the /opt folder but am questionable about /var because of it's similarities to /usr in that it contains variable data by programs.

Are there any other folders that can be shared as well such as /etc?
[/LEFT]

---

### Post by ottosykora on 2011-01-04
well usr is something like the system folder of windows, so if you can share the window system between w7 and vista then...

similar with all others , boot is the loader of the particular system

Some people share the home, but this is problematic if you have users having same name on all distros. It hold also configuration of lot of thigs, so works only if the distros are kind of similar.
opt could work, but here apps are put and again it may then not work if the distro is not able to run such app because of some dependencies.
Sharing var will certainly bring confusion too, logs and other things will never be correct.

you can have certainly only one swap on whole computer, made as one small swap partition.

---

