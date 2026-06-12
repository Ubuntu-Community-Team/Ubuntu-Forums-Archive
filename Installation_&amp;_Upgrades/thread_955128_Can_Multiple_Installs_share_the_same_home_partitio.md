---
title: "Can Multiple Installs share the same /home partition?"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by Ng Oon-Ee on 2008-10-21
Hi guys,

Am planning my upgrade-path to Intrepid, and I've been considering the above. I already have a separate /home partition, and a working Hardy install. Would like to test Intrepid, but with a 'fallback' option to Hardy if I mess things up by poking around (as is very likely).

However, I really don't want to have to re-run a lot of the customization/setup steps I've done on my Hardy install. Is it possible to select my current /home partition as the home partition (without formatting) for Intrepid, and for both Intrepid and Hardy to access that same /home partition? Should I expect incompatibilities due to Intrepid's changes when I boot back into Hardy?

Thanks in advance.

---

### Post by ilrudie on 2008-10-22
Yes its possible.  Its probably not the best idea because the newer apps may indeed make new incompatible changes to config files in your home.  Maybe just make a copy of your home folder called <username>_ii and when you make your new user in Intrepid just make sure you use that folder as your home folder.  As always its a good idea to backup anything you can't stand to lose when doing this.

---

### Post by Ng Oon-Ee on 2008-10-22
Thanks for the reply ilrudie.

I've been reading up semi-related stuff online, it seems one of the big problems would be different UIDs for the same username in different distros (not an issue for different releases of Ubuntu I hope) as well as newer versions of apps which change config files to be unrecognizable by older versions (firefox 3 vs firefox 2 for example).

There was even a guide as to how to symlink only the components you'd want to keep (yet without a list of files which should be kept, i suppose this depends on your config).

Any additional help is deeply appreciated, everyone. As of now, I'm in the process of cleaning up my home folder so that it contains only things that can't be moved out (I have this bad habit of installing programs into the home folder). For example, I have multiple Wine directories that have been moved to my data store.

---

### Post by ilrudie on 2008-10-23
UID is not a problem at all.  Its very easy to change with the usermod command.
```
sudo usermod -u <newUID> <yourUserName>
```
If you decide to make you user the old-fashioned way (a.k.a. from the command line) its settable while you are setting up the user too.  The only issue you can run into is anything your user used to own is still owned by your old UID not your new one so you have to chown [-R] it.  Not a big deal though really.  You shouldn't own much outside your home anyways.

---

### Post by Kobalt on 2008-10-23
Usually, when testing a distro I know I won't keep long I use the same /home partition but I create a new user for that distro, so that I don't mess with my proper user settings and data. Later on you can easily delete the created user folder anyway..

---

### Post by Ng Oon-Ee on 2008-10-23
Thing is, my main reason for testing distros is to prepare for an upgrade (for example, from Hardy to Intrepid), so if things work well I WILL be moving over.

Maybe I should spend some time just going through the whole home directory and figuring out what's important/not.

---

