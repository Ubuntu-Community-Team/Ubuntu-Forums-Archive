---
title: "Would I have to do a clean install?"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by h3llh0l3 on 2008-10-31
Hello all,

I was running ubuntu hardy LTS server. I followed the steps here [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) and did a network upgrade for ubuntu servers.
After the upgrade finished it had removed KDE 3.5 and lots of other things. A total of 935 packages were removed. So after the upgrade finished I restarted the computer and tried installing KDE, which installed fine. And after reboot when I tried logging in the KDE loading box(not sure what it is called, just moved to linux) stops at the 4 icon and nothing happens. I can't even get to the CLI by pressing Ctrl + Alt + F1 thru F6.
So, I restarted the computer and with out logging in thru the splash screen I switched to CLI where I tried executing commands like updatedb, locate and got a reply stating that the command was not found.
I am not sure as of now what all trouble is there with the current intrepid upgrade. Is there a way to check the upgrade logs and try to fix it? Or would I have to do a clean install. I'am in the process of downloading the ubuntu intrepid.

But I would like to fix this without going thru the clean install as I think I would get to learn a lot from this. Help appreciated.

Thanks :)

---

### Post by h3llh0l3 on 2008-10-31
Anyone, any thing that I can do to fix this? I have burnt the intrepid disk just waiting to see if this can be fixed without going thru the clean install.

Thanks.

---

### Post by andreselsuave on 2008-10-31
Maybe you can try to install ubuntu-desktop from the apt-get manager from the command line... (Im gnome user) and then you log into gnome and you can try reinstalling kde

---

### Post by h3llh0l3 on 2008-10-31
> **andreselsuave said:**
> Maybe you can try to install ubuntu-desktop from the apt-get manager from the command line... (Im gnome user) and then you log into gnome and you can try reinstalling kde

Thanks for the reply.
I am actually not much concerned about KDE not working. But what I am interested in is to know what all was done on the system during the upgrade. Some sort of a log. Most of the commands are not working as of now. And I would like to know why?

Currently I am doing network upgrade on another computer of mine and tell you what, its going real smooth. It downloaded all the packages that it had to and is unpacking them and installing them. Both machines that I have are replica of each other in all aspects.

But on this one I was not prompted that 900 odd programs would be removed. Just waiting for this complete. If this also gets screwed then I will have 2 machines to take care of. {Crossed fingers}

So, is there a way to get to the logs?

Thanks.

---

### Post by Partyboi2 on 2008-10-31
try looking in /var/log/dist-upgrade :)

---

### Post by h3llh0l3 on 2008-10-31
> **Partyboi2 said:**
> try looking in /var/log/dist-upgrade :)

Thanks. I will look into it and see if I can figure this out. Will post back if I have hard time. Thanks again.

---

