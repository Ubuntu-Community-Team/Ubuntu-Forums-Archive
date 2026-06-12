---
title: "Install from dwloaded pkg saved in HDD"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by arjunajay on 2008-07-09
Hi,
I'm new to Ubuntu.My version is 8.04
1) I download tar.gz files of apps that i want to install. eg for blender and ffx. How do I tell Add/Remove or the synaptic package manager to install the app/library from the downloaded (tar.gz) file rather than from the internet or from the DVD?
This is because I frequently install and uninstall apps and i don't want the files to be downloaded from the net (as it is slow and cause me to exceed my download limit).

2) My Add/Remove still shows gcc, g++ to be 4.2 as it is probably the one in the DVD. How do I tell it to show the most recent version (which is something like 5.x)? There is also an entry there which shows 'gcc' (without version number). Is that it?

---

### Post by iaculallad on 2008-07-09
> **arjunajay said:**
> Hi,
I'm new to Ubuntu.My version is 8.04
1) I download tar.gz files of apps that i want to install. eg for blender and ffx. How do I tell Add/Remove or the synaptic package manager to install the app/library from the downloaded (tar.gz) file rather than from the internet or from the DVD?
This is because I frequently install and uninstall apps and i don't want the files to be downloaded from the net (as it is slow and cause me to exceed my download limit).

With the tar.gz archived file, you have to do the installation manually. Extract the archive and do the usual process of:

```
cd extracted_archive_directory
./configure
./make
./install

```

Or try reading the readme file w/c comes with the archive file.


> **arjunajay said:**
> 2) My Add/Remove still shows gcc, g++ to be 4.2 as it is probably the one in the DVD. How do I tell it to show the most recent version (which is something like 5.x)? There is also an entry there which shows 'gcc' (without version number). Is that it?

Maybe, the system needs a restart in order for the version number to initialize :)

---

### Post by arjunajay on 2008-07-10
I probably wasn't clear.
I downloaded **Pre compiled Binaries**.
I haven't got enough experience to build on my own (Yet).

---

### Post by iaculallad on 2008-07-10
> **arjunajay said:**
> I probably wasn't clear.
I downloaded **Pre compiled Binaries**.
I haven't got enough experience to build on my own (Yet).

Pre-compiled binaries:

For .deb files:

```
sudo dpkg -i package_name.deb
```

For .rpm files:

You need the alien utility to convert it to Debian format.

```
sudo apt-get install alien
```

To convert to .deb file:

```
sudo alien -d package-name.rpm
```

and to Install:

```
sudo dpkg -i package-name.deb
```

---

### Post by arjunajay on 2008-07-10
thanks...

---

