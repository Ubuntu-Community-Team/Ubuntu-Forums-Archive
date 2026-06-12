---
title: "Installed home folder to another partion - executable problems"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by gefalu2008 on 2010-05-04
While doing a clean install of Ubuntu 10.4 64 bit, I selected to install the home folder on a separate partition.

In an earlier version (9.10 64 bit) I used to have programs like Revolution Media and Google Earth in the home folder (that was on the same partition as the rest of the system).

Now when I install e.g. RevMedia into a folder of the home folder, the software does not respond to my efforts to launch it.

Have I somehow got the permissions wrong in the home folder? Or should I install software to another place?

I do not know where to start, so all suggestions are welcome. Thank you!

- Gef

---

### Post by cuby on 2010-05-04
How did you install those apps? You have the executable permission set in the start script or binary?

---

### Post by srs5694 on 2010-05-04
Post the output of the following command:

```

grep home /etc/fstab

```

It's possible that you need to adjust a mount option, which will be revealed by this command.

---

### Post by gefalu2008 on 2010-05-04
The output is as follows:

gef@gef-hp:~$ grep home /etc/fstab
# /home was on /dev/sda3 during installation
UUID=f4f79c0f-4ab0-422c-9d09-23f4bffda90e /home           ext4    defaults        0       2

I installed the software [that I referred to as executables] (Revolution Media and Google Earth) by downloading to folders in the home folder and extracting the files there. This is what worked before.

Thank you for your attention. I am still at loss, so your advice is very welcome.

---

### Post by gefalu2008 on 2010-05-05
This is just to show what happens when I download Google Earth and try to install it normally:

----

gef@gef-hp:~$ cd /home/gef/downloads/
gef@gef-hp:~/downloads$ chmod +x GoogleEarthLinux.bin 
gef@gef-hp:~/downloads$ sudo ./GoogleEarthLinux.bin
[sudo] password for gef: 
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.1.3533.1731...............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!

----------

As you can see, the installer failed to run. It seems that my new home folder prevents me from running programs, but if I interpret the fstab-results correctly, executing programs is not inhibited by fstab settings. 

Similarly I have ownership & executing rights as far as I know.

---

### Post by gefalu2008 on 2010-05-05
Now I have solved the problem. The problem was that Google Earth and Revolution Media are 32-bit programs. So after I installed Medibuntu package from [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) everything went smoothly. I could install Google Earth from Synaptic and RevMedia works fine.

Thank you, everyone!

- Gef

---

