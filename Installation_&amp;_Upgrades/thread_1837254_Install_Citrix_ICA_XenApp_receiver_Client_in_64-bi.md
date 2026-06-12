---
title: "Install Citrix ICA XenApp receiver Client in 64-bit Ubuntu 11.04 Natty"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by odinb on 2011-09-01
See lots of other users having problems with the Citrix receiver on 64-bit Natty, so here goes:

Because we are on 64-bit Linux, we only have 64-bit libraries.
Install the 32-bit libraries with:
```
$ sudo apt-get install libxaw7 libmotif4 ia32-libs
```

ICA Client needs the OpenMotif 2.3 libraries (often called OpenMotif version 3, or libmotif4).
Go to the Ubuntu package search: [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
Under the header 'Search package directories', search for libmotif4.
Choose the libmotif4 package from natty, version at time of writing: 2.3.3-5ubuntu1, and download the i386 package.
Extract the package:
```
$ mkdir libmotif4
$ dpkg -x libmotif4_2.3.3-5ubuntu1_i386.deb libmotif4
```

Now copy the libraries to /usr/lib32 (make sure they don't overwrite existing files):
```
$ cd libmotif4/usr/lib
$ cp -ivR * /usr/lib32
```

This should install libXm.so.4 in the correct directory, which is needed by the ICA Client.

Go to the Citrix download page: [http://www.citrix.com/english/ss/downloads/]("http://www.citrix.com/english/ss/downloads/")
Click in the 'Featured Downloads' box on the right on the Linux Clients link.
Download the x86 client tarball. (Note: as of 25 Aug 2011 Citrix supplies a .deb as well as a .rpm and tarball. While I was able to install the .deb, I could not subsequently run the Citrix Receiver it installed. However I was able to run the Citrix Receiver successfully after installing the tarball.)

Download the linux client tarball to some temp dir, e.g. /tmp/citrix
Extract the tarball.
From the download directory, run the text-mode script:
```
$ sudo ./setupwfc
```

Take the option to "Install Citrix Receiver", then install to the default directory: /usr/lib/ICAClient

Check that the executable /usr/lib/ICAClient/wfcmgr was created (and also Applications>Internet>Citrix Receiver, though that's just a link).

Check that the executable /usr/lib/ICAClient/wfcmgr has needed libraries:
```
$ CLIENT_EXEC="/usr/lib/ICAClient/wfcmgr"
$ ldd ${CLIENT_EXEC}
```

You should get results like: 
```
	linux-gate.so.1 =>  (0xf7718000)
	libXm.so.4 => /usr/lib32/libXm.so.4 (0xf74a6000)
	libXp.so.6 => /usr/lib32/libXp.so.6 (0xf749d000)
	libXpm.so.4 => /usr/lib32/libXpm.so.4 (0xf748c000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7484000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf746c000)
	libXmu.so.6 => /usr/lib32/libXmu.so.6 (0xf7456000)
	libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf7451000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf744d000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7434000)
	libc.so.6 => /lib32/libc.so.6 (0xf72d7000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf7285000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf716a000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf715a000)
	libXft.so.2 => /usr/lib32/libXft.so.2 (0xf7146000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7142000)
	libuuid.so.1 => /lib32/libuuid.so.1 (0xf713d000)
	/lib/ld-linux.so.2 (0xf7719000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf7124000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf70f4000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf706e000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf7064000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf705e000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf7049000)
	libexpat.so.1 => /lib32/libexpat.so.1 (0xf701e000)

```

If you get a "not found" above, you have missed one of the earlier steps of installing 32-bit libs.

If not, try just running /usr/lib/ICAClient/wfcmgr: if that launches the Citrix Receiver, you're done!

For Terminal server, at first launch, Firefox will ask you what to do with the launch.ica file. Choose "Open with" and click the "Browse" button. Browse to /usr/lib/ICAClient/ and click the "wfica" binary.

If you do not want to have to do this every time, tick the box that says "Do this automatically for files like this from now on.", then click "ok".

Terminal server should now work.

---

### Post by Reg71 on 2011-09-01
had to come back and edit this as I am further in the installation, but not working yet...

when I try to run it, I get:

/usr/lib/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.4: cannot open shared object file: No such file or directory

so I'm guessing I'm not doing the libraries right.  I have them downloaded and extracted, but I don't seem to have a /usr/lib32 folder.  I installed 11.04, but is there a 32 and a 64 bit version?  How do I know which I have?  All I can find is that it's 11.04 in my menus and such.

---

### Post by Reg71 on 2011-09-01
Ok, I'm talking to myself at this point, but in case anyone runs into the same issue I did...

#sudo apt-get install libmotif

worked to get the libraries in the right place.  Now I it will run, but I get a popup that says "PnaAuthDialog_popup" and it is blank other than the handle.  This is trying to get to my workplace through Firefox.  If I try it through Chrome, I get a "Missing Plugin".  

I may keep playing around a bit or just quit for a while, but I'll post back if I get any further.

---

### Post by odinb on 2011-09-02
Doing:
```
$ uname -a
Linux mymachine 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

You will see if you have 32 or 64 bit, the "x86_64" part tells you it is 64 bit.

Also, did you run the following command:
```
$ sudo apt-get install libxaw7 libmotif4 ia32-libs
```

from the guide?

It should install the needed 32 bit libs (except for 32 bit libmotif) for you automatically, and the /usr/lib32 directory is created at that point.

---

### Post by akshunj on 2012-01-01
Thankfully this workaround is no longer necessary. As of October, Citrix has a 64 bit receiver client packaged as a .deb. ;)

---

### Post by Mars73 on 2012-01-12
Not sure if you still don't need the motif thing with the 64 bit client but having a few years of 'experience' with citrix clients and linux it was not a lot of trouble to install.
What was a lot of trouble was that I had an unstable citrix connection from my home to my companies citrix access gateway. The connection was constantly disconnected while there was no problem with my or my company's connection.
After many many trials and error I found out network manager was the culprint. I installed wicd and completely removed everything that had to do with networkmanager and my remote Citrix connection (and I) has been happily connected for longer periods.
Anyway, wanted to share it as I'll probably won't be the only one with the problem. (though I couldn't find anything about it).
If ever installing a new version of Ubuntu (or Mint), first thing I'll do is ditch networkmanager.

---

