---
title: "Ubuntu 10.04 GDM/Gnome Login Loop"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by axi0n on 2010-03-19
I found this via the long waaaay around...   I originally patched some 10.04 .debs onto 9.10 (ProFTPd and OpenSSH) to pass some security audits @ work...   Then had to fufill some other dependencies to get them installed...

Finally worked but needless to say it broke a lot of other things on the system...

After 10+ hrs of fumbling through logs, etc, I think I have discovered an unresolved dependency check...

I dowloaded the latest daily Lucid ISO i386, managed to patch the system mostly via apt-get -f install after adding the cd to my sources.list

On reboot, I would be presented with the GDM login screen but when I clicked on a user and entered a password.. it would look like it was logging in, then kick me straight back out to the login screen...

Looking at the logs, I eventually figured I would attempt to re-install the complaining packages with....

sudo apt-get install xxx --reinstall --force-yes

I had done a bunch when I tried to re-install gnome... It was already installed but said it couldn't re-install because of a missing dependency...  Empathy...

sudo apt-get install empathy

It also had a recommendation to install "gnome-desktop-environment"  (well duh.. ) ;-)

Installed that... Plus the bonus 112Mb of dependency packages, and now I am fully into the system GUI...

Hope this helps...

Cheers,

Ax.

---

### Post by phillw on 2010-03-19
Hi and welcome to the forums,

Well.... I guess that's one way of doing it.

Remember that 10.04 is in testing, and should not be running as a production machine (It may get broken during its development).

But, you're on 10.04 (ish) :-)

Pop on over to [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377) which is the forum for Lucid. Take the time to read the stickies :-)

You can bring your system fully to 10.04, if you want, but have a read through the posts and see if there any things that may cause you problems.

Happy testing !

Regards,

Phill.

---

### Post by axi0n on 2010-03-20
Ya, it was folly to update... Especially packages like Libc6.. Sure ProFTPd and OpenSSL managed to go in without complaints after I put in 18 or so low level dependencies but it broke A LOT of other things...

Then because I had updated a bunch of other core packages, to remove them meant I was looking at an insane # of recursively dependent packages  that would be removed if I tried to get rid of the new core packages...

I really didn't want to start forcing things without dependency checks, it would be too easy to miss things and end up in a similar situation. So I figured at this point updating to 10.04, which is where I had pulled the updated .debs in the first place (except for php 5.3.2) was my sanest choice...

So... Not sure how relevant my discovery might be, though I had discovered more than a few similar situations when searching Google...

Luckily, even with Gnome/X/GDM broken... SSH, syslog-ng, Apache2, PHP5 and PHP-Syslog-NG still functioned, so it was never really down and out...   Not to mention, its a syslog server..   The people who should have been using it got in the habit of *NEVER* checking it until there were issues afoot...

One more server to go... This one will be snapshot'ed regularly at signs of positive forward progress until everything is resolved...   ;-)   

Lesson learned...

All I can say re: 10.04... I knew it wasn't going to be, but I was still subconsciously expecting Brown....   Now there is this purple fruity number wallpaper...

---

