---
title: "How to Install OpenVPN Admin"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by junkam on 2008-06-13
I'm installing a new machine with ver 8.04, but I can not find the openvpn-admin package.
On 7.04 I had this package available in the repository. How can I get it to work on 8.04 ??

Any help is appreciated, this is very important to me

---

### Post by kdcoetzee on 2008-06-13
[URL="https://wiki.ubuntu.com/VPN"]https://wiki.ubuntu.com/VPN
[/URL]

I don't know of a admin package.
But if you want you can install with the packages on that site.

---

### Post by Homer on 2008-09-16
> **junkam said:**
> I'm installing a new machine with ver 8.04, but I can not find the openvpn-admin package.
On 7.04 I had this package available in the repository. How can I get it to work on 8.04 ??

Any help is appreciated, this is very important to me


The mono package  seem to have been renamed in hardy.  If you have mono installed, you just have to force the installation of the deb package :

```
dpkg -i --force-deps openvpn-admin-xxxxx.deb
```

It's how I installed it and it works !

---

### Post by Ankel_CZE on 2008-09-19
> **Homer said:**
> The mono package  seem to have been renamed in hardy.  If you have mono installed, you just have to force the installation of the deb package :

```
dpkg -i --force-deps openvpn-admin-xxxxx.deb
```

It's how I installed it and it works !

Yes, this works, but seems to iritate apt and synaptic. On next install/remove via apt, it marked openvpn-admin as a must remove package, because it requires mono, that is no more "installable". Is there a way to tell apt to don't worry about this forced package?

```
echo openvpn-admin hold | dpkg --set-selections
```

didn't help. Or is there a way of rebuilding a package dependencies in a openvpn-admin.deb ?

EDIT: I remove the "old-named" mono package from dependency control list of a original .deb .Now apt is happy, and synaptic show the package as "local".

---

### Post by TuxOtaku on 2009-02-25
> **Ankel_CZE said:**
> 
EDIT: I remove the "old-named" mono package from dependency control list of a original .deb .Now apt is happy, and synaptic show the package as "local".

Care to share a how-to as to how you did this?

---

### Post by TuxOtaku on 2009-02-26
> **TuxOtaku said:**
> Care to share a how-to as to how you did this?

Looks like this won't be needed. I managed to figure it out on my own, so I figured I might as well share how I did it.

The first thing to do is make a folder to do all your work in, call it say, "debdump" or something. This isn't necessary, but it just helps keep things neat and tidy.

Next, you need to extract the package's contents as you would any other archive file

```
ar xv openvpn-admin.deb
```

dpkg has tools to do something similar, but they didn't seem to work for me.

If you've never seen the contents of a deb package before, it's actually surprisingly simple. You have three main files: *control.tar.gz*, *data.tar.gz*, and *debian-binary*. *Control.tar.gz* contains scripts and other files that tell the package where to put everything, and what the package depends on, while *data.tar.gz* is just as its name suggests; it's the actual program files. *Debian-binary* just tells dpkg what version of dpkg was used to build the package.

So, since in our case, we have a broken dependency, we need to extract the contents of *control.tar.gz*.

However, due to how dpkg works regarding BUILDING packages, first we need to create a folder called DEBIAN (this is case-sensitive, it MUST be all-caps).

Now extract control.tar.gz into the DEBIAN folder and move data.tar.gz and debian-binary into that folder as well.

once in the DEBIAN folder, you'll see a bunch of files. We're interested in one called "control". Open control in a text editor, and scroll through to the following section:

```
Depends: mono-runtime (>= 1.0), libglade2.0-cil (>= 2.7.90), libglib2.0-cil (>= 2.7.90), libgtk2.0-cil (>= 2.7.90), libmono-corlib1.0-cil (>= 1.0), libmono-system1.0-cil (>= 1.0), libmono1.0-cil (>= 1.1.17.1), libx11-6, openssl (>= 0.9.8a-5), mono (>= 1.1.10-1), openvpn (>= 2.0.5-1)
```

The dependency we want to remove, is "*mono (>= 1.1.10-1)*", so delete it, save the file, and close the text editor.

Now we move on to the fun part, building the package.

cd back up to the folder just above "debdump" or whatever you called your work directory, and issue the following command (as root).

```
dpkg -b debdump openvpn-admin.deb
```

dpkg will then build the package and now all you have to do is *dpkg -i openvpn-admin.deb*, and you're in business. No dependency errors, nothing.

---

### Post by cjohnson19791979 on 2010-08-23
hey tux i've just installed version 10 and the whole package re-build seemed to go well. the package install seems to go well also. the problem i've got though is that it's not actually installing anything. for example /usr/sbin/openvpn-admin isn't being created. i assume this is because i must have borked something during the package re-build but i dunno. can you (or anyone for that matter) be of any help?

---

