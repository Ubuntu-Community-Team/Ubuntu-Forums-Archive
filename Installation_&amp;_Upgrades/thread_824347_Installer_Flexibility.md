---
title: "Installer Flexibility"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by atoponce on 2008-06-10
I teach Linux for a living.  Mainly system administrators are my students, and Red Hat is the main operating system taught.  I work for [Guru Labs]("http://gurulabs.com"), based out of Utah, United States, and can't imagine working for a better company (except for maybe Canonical :)).

As such, with my instruction, I take extensive advantage of the flexibility that the Red Hat installer, Anaconda, gives me.  I can boot Anaconda from USB, CDROM, GRUB, and the network.  Further, I can install software from HTTP, FTP, NFS, CDROM and HDD.  I can point Anaconda to *.iso images or a YUM repository to get the software.  With this extensive flexibility, I am incredibly impressed with Anaconda.  Which brings me to the point of my post.

As I understand, I can only boot from a CDROM or the network, and I can only get software from the CDROM or an HTTP repository.  Further, I can't point the Debian installer to *.iso files to get the software, so booting from a CDROM, and pointing it to an *.iso file on my external hard drive is out of the question.

Automating an Anaconda install with Kickstart is amazing, and the fact that Anaconda builds a /root/anaconda-ks.cfg of the *exact* install I just performed automatically for me rocks.  Cloning that machine is as simple as making the Kickstart file available to the remainder of the machines I need to build, either via NFS, HTTP, or other means, and I'm off.  Preseed needs work, or Ubuntu should fully support Kickstart.

I guess the whole thing I'm getting to, is when can I expect to see more flexibility in the Debian installer, or the Live installer?  Is this something that's being worked on or addressed?  Will Ubuntu strive to become an administrator's first reach for easy installs, or will Red Hat be the first choice?  I really would hope that it's Ubuntu.

Anyway, just something that I had to get off my chest.  We will be teaching Ubuntu courses soon, and installing classrooms with 20 machines as quickly as possible (under 1 hour) is critical to our effectiveness as an instructor in the classroom.

---

### Post by hal8000 on 2008-06-10
This is all fine and well when Anaconda works well with your hardware and software, but I've had errors with Anaconda when installing Fedora, Foresight Linux and any other distro that uses it.

The problem with any installer is that it has to be flexible enough to install the system, and work with as many combinations of hardware and software as possible. The more complex an installer, the more there is to go wrong.

Personally I think the Ubuntu installer is about right, the partitioner (gparted) still wont recognise Solaris and FreeBSD partitions (but there are ways around this problem) and once youre past partioning, installation is fairly painless.

The standard Debian installer is very basic and text based, this makes it difficult for a beginner to install, but theres very little to go wrong.
If Debian had a graphical installer and setup tools, it would probably be a lot higher in its ratings.

Thats a good post and I never knew the other abilities of Anaconda. Its also a while since I tried Fedora (last version being 6) so probably the Anacaonda installer has also matured since then as well.

---

### Post by atoponce on 2008-06-10
Well, it's not so much hardware recognition, as that's handled by the kernel and the modules loaded by it.  If the current installer can recognize all the hardware appropriately, the certainly there could be more flexibility in *how* the install is performed, and where the software comes from for the installation.  i can't see how the installer and hardware recognition are really intertwined.

---

