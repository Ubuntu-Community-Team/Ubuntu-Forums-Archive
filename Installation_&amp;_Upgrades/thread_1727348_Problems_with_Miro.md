---
title: "Problems with Miro"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2011-04-12
Hello,

I have a high speed Internet connection, and just lost cable TV due to my cable provider's recent conversion to digital.  I now have to put down an $80.00 deposit and rent their converter-box montly, or go without TV. Frankly, I would; but ocassionally I need a break from coding, and all the other stuff I do on my PC.  So, I've been investigating IPTV.

I recently tried installing "Miro" from the repsoitories. That gave me an error message indictating that the dependencies could not be satisfied, because of an incompatible package that was already installed. Unfortunately, 'Software Center' didn't even give me a clue about what package that might be...  I recall reading somewhere that it might have something to do with X11 & Python.  In parallel, I tried compiling "FripTv," and had to disable the WxWidgets features, to get the source to compile without errors.  Then when I tried to run it, all I got was a blank screen.  Maybe these two issues are related?

I then added Miro's current respositories to my software-sources, and it installed corectly; however, when I tried to download a program to watch, the program would download for a while, and then Miro would just freeze.  I then had to perform Euthenasia on the process, to get Miro to shut down.  I've just finished building and installing WxWidgets 2.9.1 from source.  This proceeded without any difficulties.  Now I'm going to try 'both' methods of installing Miro again to see what happens.

Can anyone help shed some light on what might be going on here?  It's my understanding that Debian based OS's like Ubuntu, are less tolerant of some applications than many other Linux distro's.  Also, it's been my experience that when the vendor warns, 'not' to use the repositories and 'build from sorce;' I had better darn-well do that, if I want things to go well.

In the meantime, can anyone suggest another IPTV client that will work with Maverick?


Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2011-04-12
Oh here's something:

```
sophie@sophie-laptop:~$ ***sudo apt-get install miro***
Reading package lists... Done
Building dependency tree       
Reading state information... Done

_The following packages were automatically installed and are no longer required:_[B][I]
  codeblocks codeblocks-common libmgl-data libcsiro0 libplplot-c++9c2
  libnewpki2 libcodeblocks0 libplplot9 libmgl5 libqhull5[/I][/B]

Use 'apt-get autoremove' to remove them.

_The following extra packages will be installed:_[B][I]
  ffmpeg2theora miro-data python-libtorrent[/I][/B]

_The following NEW packages will be installed:_[B][I]
  ffmpeg2theora miro miro-data python-libtorrent[/I][/B]

0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,058kB of archives.
After this operation, 11.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Get:1 [http://ppa.launchpad.net/pcf/miro-releases/ubuntu/](http://ppa.launchpad.net/pcf/miro-releases/ubuntu/) maverick/main miro-data all 3.5.1-1ubuntu1~pcf2~maverick [1,963kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe ffmpeg2theora amd64 0.24-2build3 [29.7kB]
Get:3 [http://ppa.launchpad.net/pcf/miro-releases/ubuntu/](http://ppa.launchpad.net/pcf/miro-releases/ubuntu/) maverick/main python-libtorrent amd64 0.15.5-0ubuntu1~pcf1 [504kB]
Get:4 [http://ppa.launchpad.net/pcf/miro-releases/ubuntu/](http://ppa.launchpad.net/pcf/miro-releases/ubuntu/) maverick/main miro amd64 3.5.1-1ubuntu1~pcf2~maverick [562kB]

Fetched 3,058kB in 19s (161kB/s)                                               
Selecting previously deselected package ffmpeg2theora.
(Reading database ... 437893 files and directories currently installed.)
Unpacking ffmpeg2theora (from .../ffmpeg2theora_0.24-2build3_amd64.deb) ...
Selecting previously deselected package miro-data.
Unpacking miro-data (from .../miro-data_3.5.1-1ubuntu1~pcf2~maverick_all.deb) ...
Selecting previously deselected package python-libtorrent.
Unpacking python-libtorrent (from .../python-libtorrent_0.15.5-0ubuntu1~pcf1_amd64.deb) ...
Selecting previously deselected package miro.
Unpacking miro (from .../miro_3.5.1-1ubuntu1~pcf2~maverick_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for menu ...
Processing triggers for shared-mime-info ...

Unknown media type in type 'chemical/x-alchemy'
Unknown media type in type 'chemical/x-cache'
Unknown media type in type 'chemical/x-cactvs-ascii'
Unknown media type in type 'chemical/x-cactvs-binary'
Unknown media type in type 'chemical/x-cactvs-table'
Unknown media type in type 'chemical/x-cdx'
Unknown media type in type 'chemical/x-cdxml'
Unknown media type in type 'chemical/x-chem3d'
Unknown media type in type 'chemical/x-cif'
Unknown media type in type 'chemical/x-cml'
Unknown media type in type 'chemical/x-daylight-smiles'
Unknown media type in type 'chemical/x-dmol'
Unknown media type in type 'chemical/x-gamess-input'
Unknown media type in type 'chemical/x-gamess-output'
Unknown media type in type 'chemical/x-gaussian-input'
Unknown media type in type 'chemical/x-gaussian-log'
Unknown media type in type 'chemical/x-genbank'
Unknown media type in type 'chemical/x-gulp'
Unknown media type in type 'chemical/x-hin'
Unknown media type in type 'chemical/x-inchi'
Unknown media type in type 'chemical/x-inchi-xml'
Unknown media type in type 'chemical/x-jcamp-dx'
Unknown media type in type 'chemical/x-macromodel-input'
Unknown media type in type 'chemical/x-mdl-molfile'
Unknown media type in type 'chemical/x-mdl-rdfile'
Unknown media type in type 'chemical/x-mdl-rxnfile'
Unknown media type in type 'chemical/x-mdl-sdfile'
Unknown media type in type 'chemical/x-mdl-tgf'
Unknown media type in type 'chemical/x-mmcif'
Unknown media type in type 'chemical/x-mol2'
Unknown media type in type 'chemical/x-mopac-graph'
Unknown media type in type 'chemical/x-mopac-input'
Unknown media type in type 'chemical/x-mopac-out'
Unknown media type in type 'chemical/x-msi-car'
Unknown media type in type 'chemical/x-msi-hessian'
Unknown media type in type 'chemical/x-msi-mdf'
Unknown media type in type 'chemical/x-msi-msi'
Unknown media type in type 'chemical/x-ncbi-asn1'
Unknown media type in type 'chemical/x-ncbi-asn1-binary'
Unknown media type in type 'chemical/x-ncbi-asn1-xml'
Unknown media type in type 'chemical/x-pdb'
Unknown media type in type 'chemical/x-shelx'
Unknown media type in type 'chemical/x-vmd'
Unknown media type in type 'chemical/x-xyz'
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up ffmpeg2theora (0.24-2build3) ...
Setting up miro-data (3.5.1-1ubuntu1~pcf2~maverick) ...
Setting up python-libtorrent (0.15.5-0ubuntu1~pcf1) ...
Setting up miro (3.5.1-1ubuntu1~pcf2~maverick) ...
Processing triggers for python-support ...
Processing triggers for menu ...
sophie@sophie-laptop:~$
```

---

### Post by coljohnhannibalsmith on 2011-04-12
Well,

Miro launched ok, and let me add an RSS feed; but crashed the moment I clicked "download."  I couldn't even send an error report afterward.


Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2011-04-12
Also,

Here are some old comments, from posts I found elsewhere on the web:

**[Elliot Kendall]("http://my.brandeis.edu/shared/community-member?user_id=109")**                                                   

August 30, 2007                 
01:22:55 PM                 

IPTV does work in Linux, in theory. It's not a trivial exercise getting it working, however.  The dirty secret is that the IPTV application is not really a Java  applet. The web site runs a signed Java applet which downloads and runs a  native binary, then deletes it when you're finished. If you're like me,  you will probably want to just save the native binary and run it  directly. 

 You should try to figure out whether the native app is being downloaded  or not - probably in at least one of the cases you discuss it is. As I  recall, it gets placed in some hidden directory in your home directory. I  don't remember exactly what it was called. Probably the reason the native app won't run is that you don't have the  correct shared libraries installed. The app was built in a pretty old  Linux environment, so probably you'll need compatibility libraries to  make it work on a modern distro. Oh, and the page says 1.4.1 was the latest **at one time**, which is hard to argue with.  


**[Yuriy Kozlov]("http://my.brandeis.edu/shared/community-member?user_id=31281")**                                                   

October 15, 2007                 
10:49:33 PM                 

Looks like the binary gets saved to /tmp/vfurn[randomnumber]/Instream.app/InStream but gets deleted on exit.

I got it running by installing libstdc++2.10-glibc2.2. The  program runs and shows channel listings, but I still don't get any  video.  It says no broadcast available.  It also says Now Playing:  vftp://239.1.2.15:4900/ regardless of whether I can get the applet working. Is it possible to access the video stream with another program? 


**[David Mandelberg]("http://my.brandeis.edu/shared/community-member?user_id=46579")**                                                   

April 8, 2008                 
11:21:55 PM 

I'm running Ubuntu 7.10 64-bit. The applet never worked for me, but I  was able to get IPTV working by getting the vftp executable (I don't  remember how, but probably some combination of unzip and strings). I  then downloaded old .debs of the necessary libraries (ldd helped find  them), extracted the .so's to the same directory, and wrote this script  in the same directory to run iptv automatically:

<code>
#!/bin/sh
VFTP="`dirname "$0"`/vftp"
export LD_LIBRARY_PATH="`dirname "$0"`"
exec linux32 "$VFTP" -z 0123456789abcdef...
</code>
where 0123456789abcdef... is some key that's in the applet. 


So far, this is all I'm able to find...




Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2011-04-12
And,

My ISP, Choice Communications, uses NAT.  See below:


LAN:

[SIZE=2]Typ:[/SIZE][SIZE=2]Static[/SIZE]                 [SIZE=2]IP:[/SIZE][SIZE=2]192.168.254.251[/SIZE]                 [SIZE=2]Netmask:[/SIZE][SIZE=2]255.255.255.0

[/SIZE]
WAN:

[SIZE=2]Typ:[/SIZE][SIZE=2]DHCP[/SIZE]                 [SIZE=2]IP:[/SIZE][SIZE=2]10.18.132.120[/SIZE]                 [SIZE=2]Netmask:[/SIZE][SIZE=2]255.255.192.0[/SIZE]                 [SIZE=2]Gateway:[/SIZE][SIZE=2]10.18.132.120[/SIZE]


From: [http://whatismyipaddress.com/](http://whatismyipaddress.com/)

**[SIZE=2]IP Information:  66.185.45.235 [/SIZE]**

                                      [SIZE=2]ISP:[/SIZE][SIZE=2]Choice communications, LLC[/SIZE]                     [SIZE=2]Organization:[/SIZE][SIZE=2]Choice communications, LLC[/SIZE]                     [SIZE=2]Connection:[/SIZE][SIZE=2]
[/SIZE]                                          [SIZE=2]Proxy:[/SIZE][SIZE=2]Suspected Network Sharing Device[/SIZE]                                         [SIZE=2]City:[/SIZE][SIZE=2]St Thomas[/SIZE]                     [SIZE=2]Region:[/SIZE][SIZE=2]
[/SIZE]                     [SIZE=2]Country:[/SIZE][SIZE=2]Virgin Islands, U.S. [IMG]http://whatismyipaddress.com/images/flags/vi.png[/IMG][/SIZE]                                                                                                    

Does being behind NAT make a difference to IPTV?



Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2011-04-12
Hello....

I may have just stumbled on to a fix...  Don't hold me to it yet, though...

Anyway, here's what happened:

I remember reading something over the last couple of days about VLC-Player being used as an IPTV client.  This got me thinking... So, I opened-up Synaptic Package Manager and typed ***"vlc"*** in the search field, hoping to find something like ***vlc-server***, or something close, expecting that the package I would need would be some kind of media server.  The closest thing I could find was something called Phonon-backend-vlc.  Believing this might be what I was looking for, I installed it.  I also installed it's companion dbg package as well.  In fact, in desperation, I installed everything I could find with vlc attached to the name, that didn't require me to remove any existing packages.  This was a total 'Hail-Mary' play... And, I didn't expect it to work.  Frankly, I had no idea how I was going to get VLC-Player to work as an IPTV client.  I decided, I was just going to wing-it!

After I had installed all the 'vlc-goodies' I could find, I took another look at VLC-Player's control settings to see if anything had changed, anything like additional tabs, or features, etc.  Nothing did...

Then, I went back to work on some of my other projects, and just out of boredom, I decided to give *"Miro"* another try...  The program-guide loaded *'much'* faster.  I was able to select an item to watch, without causing the ap to hang, and it downloaded my selection, without the slightest hint of complaint.  In fact, my video selection even opened in full-screen mode only a beat after I clicked on it.. As a matter of fact, I'm watching that video right-now, and only paused it, to make this entry.  I also took two screenshots of the items I selected in Synaptic, with the intent of attaching them to this post.  I needed to take two, because not all of the selected entries would display on the screen.  Hopefully someone smarter than myself will figure-out what it was I did, that suddenly got this ap to start working...


If someone does figure it out, please post the answer here...



Thanks, Hannibal):P

---

### Post by coljohnhannibalsmith on 2011-04-13
Still working fine after 24 hours, so I'm marking this thread as solved...


Please, still do make coments.



Hanninal:popcorn:

---

