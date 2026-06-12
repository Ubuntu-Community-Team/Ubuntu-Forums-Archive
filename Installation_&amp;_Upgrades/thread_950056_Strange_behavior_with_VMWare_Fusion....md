---
title: "Strange behavior with VMWare Fusion..."
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by yrrej on 2008-10-16
Hi,

I am (trying) to run 8.04 1 on a MacBook Pro ( 2.4 GHZ Santa Rosa Chipset) under
VMWare Fusion 2.0.

For reasons that are not clear to me, downloading some deb files during an
upgrade via synaptics or the update manager appear to be corrupted...

The error message asserts that a corrupt tar file was found during the
dpkg --unpack phase.

Deleting the deb from the archive directory and repeating the download
does no good...same problem.

Now if I successfully upgrade the package on a different VM then I can
"copy" the "good" deb to the archive directory and then when I pull the
trigger on an update the new deb file will "work".

Of course if I get the same problem on both VM's then I am stuck.

I would like to try to download the offending deb outside of the VM
environment, ie directly to my MacBook Pro and then copy the deb
into the VM archive directory...

Regrettably, I can't find a "source" that will allow me to download
the appropriate deb file.

Where are the rascals hidden and how can I get the deb?

Thanks

Jerry

---

### Post by Partyboi2 on 2008-10-16
Have you tried [[COLOR=Blue]ubuntu packages[/COLOR]]("http://packages.ubuntu.com/")

---

### Post by yrrej on 2008-10-16
> **Partyboi2 said:**
> Have you tried [[COLOR=Blue]ubuntu packages[/COLOR]]("http://packages.ubuntu.com/")

Thanks...

I was able to "find" all of the packages at the above site.

In addition when I downloaded to my mac and then transfered to
the VM and copied to the archive directory the updates "worked"
every time !

Tain't clear how to handle problem downloads with multiple 
dependencies.

It took a while to get a new kernel in place...

Jerry

---

