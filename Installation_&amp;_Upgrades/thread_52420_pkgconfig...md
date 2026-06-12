---
title: "pkgconfig.."
date: 2005-07-27
forum: Installation &amp; Upgrades
---

### Post by karmah on 2005-07-27
Ok, I posted a thread earlier about PKG_CONFIG_PATH which no-one replied to but now I've learned more about it and I've found out something this time.
even though glib-2.0.pc is in /usr/pkgconfig, the program cannot find it, or thinks it has a different version( And yes, glib 2 is installed ;|). And this happens for more programs than glib...I can't install anything cuz it says I don't have the programs. here's a screenie -> [http://karmah.profundum.org/screens/Screenshot-h4xx0r3r.jpg](http://karmah.profundum.org/screens/Screenshot-h4xx0r3r.jpg)

or two..

[http://karmah.profundum.org/screens/Screenshot-daah.jpg](http://karmah.profundum.org/screens/Screenshot-daah.jpg)

Very annoying :/

I would appreciate help more than gold! ;<
Please, help me!
Thx for taking your time.

---

### Post by Xian on 2005-07-27
[QUOTE=karmah]here's a screenie -> [http://karmah.profundum.org/screens/Screenshot-h4xx0r3r.jpg](http://karmah.profundum.org/screens/Screenshot-h4xx0r3r.jpg)[/QUOTE]
Your actual configure error (the rest are only warnings) is that it is unable to find your libcurl headers. That is the only real "blocker" in what you have posted. It is easily fixed by adding the needed package (see below).

The other warnings can be repaired by just installing similar dev packages.
An example of this would be beep-media-player-dev.

EDIT: And make sure you already have the build-essential pkg installed.

```
$ sudo apt-get install libcurl3-dev
```

---

### Post by karmah on 2005-07-30
[QUOTE=Xian]Your actual configure error (the rest are only warnings) is that it is unable to find your libcurl headers. That is the only real "blocker" in what you have posted. It is easily fixed by adding the needed package (see below).

The other warnings can be repaired by just installing similar dev packages.
An example of this would be beep-media-player-dev.

EDIT: And make sure you already have the build-essential pkg installed.

```
$ sudo apt-get install libcurl3-dev
```[/QUOTE]

I see.. I tried but it didn't work.
```

# apt-get install libcurl3-dev
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libgtk2.0-0: Depends: libgtk2.0-bin (>= 2.6.8-1) but 2.6.4-0ubuntu3 is to be installed
  libgtk2.0-0-dbg: Depends: libgtk2.0-0 (= 2.6.4-0ubuntu3) but 2.6.8-1 is to be installed
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.5.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

The real problem seems to be that pkgconfig can not find the .cp files that i have, I've tried changing the PKG_CONFIG_PATH to the folder where I have them but nothing changed.

Cuz I really do have those packages installed :/. Thx for your help anyways!!

---

### Post by karmah on 2005-07-30
:O
[http://karmah.profundum.org/Screenshot-Summary.png]("http://karmah.profundum.org/Screenshot-Summary.png")

I feel like I have done something I shouldn't :S

(I chose 'fix broken packages')

---

### Post by Xian on 2005-07-30
Open Syanptic and goto the 'Status' section.
Look in the 'Installed (Local or Obsolete)' listing.

Scrutinize every package & note particularly if it is not from an official repo.
Those kind of pkgs can cause similar system-wide issues.

I've seen it a lot with some 3rd-party libc6 versions.

---

### Post by karmah on 2005-07-30
Sounds like a very good idea, though I'm a bit nooby and do not know what scrutinize is ^^
Would you please tell me? :D

---

### Post by Xian on 2005-07-30
[QUOTE=karmah]Sounds like a very good idea, though I'm a bit nooby and do not know what scrutinize is ^^
Would you please tell me? :D[/QUOTE]
Scrutinize means to assume that any package you have which was installed from a source that is not an official ubuntu repository, for example ftp.nerim.net, should be considered to be candidate for your system-wide issue with apt. Attempt to remove or replace it with an officially sanctioned version.

Backports are considered official and you can exclude them.
You really shouldn't have too many of these laying around....

---

### Post by karmah on 2005-07-30
I see. Now I know I seem to be asking you guys here on the forum for help as soon as I run into a problem but I do actually try to figure out things for myself!

Now I really can't find any way to see what repository the packages come from :/

If it is in the maintainer field in the properties>common, everything there comes from debian.org. But I guess it's not.

Or is it? :(

Your help is so very appreciated :).

---

### Post by Xian on 2005-07-30
[QUOTE=karmah]Now I really can't find any way to see what repository the packages come from :/[/QUOTE]
The only packages you even need to consider in the Synaptic module that I described are those without the 'ubuntu' and/or 'ubp' notation in the 'Installed Version' heading. Just scroll down the list. There should not be many of these to sort out.

---

### Post by karmah on 2005-07-31
Aha! I see! thx.

None of the files in Installed (Local or obsolete) have Ubuntu or ubp after the version (they are like 20) :O Uh-oh....

---

