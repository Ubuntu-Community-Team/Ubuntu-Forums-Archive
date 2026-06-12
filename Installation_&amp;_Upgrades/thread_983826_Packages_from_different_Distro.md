---
title: "Packages from different Distro"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by RealG187 on 2008-11-16
[http://bestwikiever.wikidot.com/ubuntu:local-repository](http://bestwikiever.wikidot.com/ubuntu:local-repository)
[http://kubuntuforums.net/forums/index.php?topic=3087550.0](http://kubuntuforums.net/forums/index.php?topic=3087550.0)

If I would do the steps there, but let's say use "debs_for_hardy" on a gutsy or 8.10 system what would happen? I know I am using an older version of Wine and I don't think for most programs like media players it's fine,as long as one doesn't mind older versions.

But what would happen if I tried to install my kubuntu-desktop package (made on 8.04) to my IBM machine running 7.10 or a machine running any other version, such as 8.10?

Would it successfully install the package or would it fail and possibly mess up my system? Or would I get the latest Kubuntu (8.10) and still have the Ubuntu I had before (6.10).

Because I have my 6.10 machine and I don't wanna upgrade it to 8.04 or 8.10 (Laptop at 8.04, I will not upgrade that after it comes back from repair).

Or do I have to get new packages for every version?

---

### Post by taurus on 2008-11-16
If you try to install a newer program on an older release, the program would try to upgrade all the dependencies to the newer versions and that could cause some major problems, especially if you the library files get upgraded.  That's why it's not always a good idea to mix one program from one release with another release.  It could work but soon enough, things will break.

---

