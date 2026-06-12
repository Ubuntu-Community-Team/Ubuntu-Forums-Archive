---
title: "Broken dependencies / libsuitesparse"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by jonasa on 2008-04-12
After trying to install Octave I got a problem with libsuitesparse.

I have tried a bunch of things but allways get the error:
Unpacking libsuitesparse (from .../libsuitesparse_3.0.0-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libamd.so.1', which is also in package libumfpack4
Errors were encountered while processing:
 /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

So, as some others I have tried the following:
1. Run the "Synapric Package manager" and its "Edit->Fix Broken packages"
2. sudo apt-get install -f
3. sudo dpkg --configure -a

They either try to install libsuitesparse and fail, or uggest that libsuiteparse should be installed which does not work.

Any ideas?

---

### Post by jonasa on 2008-04-13
Hi,
 would really appreciate some help. How in general should I proceed? As long as this is not fixed I can not install new software - get updates etc. 
There must be an easier way then reinstalling from scratch. Or?

Is it for example a really bad idea to erase
/usr/lib/libamd.so.1

and then try again?

Or will erasing that file create some problems?

Regards
J

---

### Post by Pumalite on 2008-04-13
Clean your cache. I think the command is:
sudo apt-get clean
You could also use:
gksudo nautilus
If the command doesn't work.
[https://answers.launchpad.net/ubuntu/+question/2978](https://answers.launchpad.net/ubuntu/+question/2978)

---

### Post by jonasa on 2008-04-13
Thankx,

I did like this:
sudo apt-get clean

This first command does exactly as suspected (it deletes the libsuitesparse file in /var/cache/apt/archives/ )

Unfortunatelly I get exactly the same error message when doing:
sudo apt-get install -f

Something else seem to be the problem.

Any other things to try?

Regards
J

---

### Post by Pumalite on 2008-04-13
Post the entire output od sudo apt-get install -f

---

### Post by jonasa on 2008-04-13
Thanks for helping: Here it comes...

sudo apt-get install -f
[sudo] password for jonasa:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsuitesparse
The following NEW packages will be installed:
  libsuitesparse
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B/898kB of archives.
After unpacking 2179kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 123554 files and directories currently installed.)
Unpacking libsuitesparse (from .../libsuitesparse_3.0.0-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libamd.so.1', which is also in package libumfpack4
Errors were encountered while processing:
 /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Regards
Jonas

---

### Post by Pumalite on 2008-04-13
Run these in sequence:
dpkg --configure -a
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update

---

### Post by jonasa on 2008-04-13
Hi again Pumaligt,
Thanks for your time and effort.

Heres the output:

sudo dpkg --configure -a
[sudo] password for jonasa:
dpkg: dependency problems prevent configuration of octave2.9:
 octave2.9 depends on libsuitesparse; however:
  Package libsuitesparse is not installed.
dpkg: error processing octave2.9 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 octave2.9

It seemed to be a problem, but I continued:

jonasa@slowfox:~$ sudo apt-get clean
jonasa@slowfox:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jonasa@slowfox:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jonasa@slowfox:~$ 

Here it seemed like a good idea to try the old

sudo apt-get install -f

jonasa@slowfox:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsuitesparse
The following NEW packages will be installed:
  libsuitesparse
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 898kB of archives.
After unpacking 2179kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe libsuitesparse 3.0.0-3 [898kB]
Fetched 898kB in 23s (38.2kB/s)                                                
(Reading database ... 123554 files and directories currently installed.)
Unpacking libsuitesparse (from .../libsuitesparse_3.0.0-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libamd.so.1', which is also in package libumfpack4
Errors were encountered while processing:
 /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jonasa@slowfox:~$


So, it seems to me something went bad during the Octave 2.9 installation.
Anyway - it did not work. Some more suggestions?

Regards
Jonas

---

### Post by Pumalite on 2008-04-13
sudo dpkg --remove --force-remove-reinstreq octave2.9
sudo apt-get update
sudo apt-get upgrade

---

### Post by bapoumba on 2008-04-13
How did you install octave?
Did you check these threads?
[http://ubuntuforums.org/showthread.php?t=713880]("http://ubuntuforums.org/showthread.php?t=713880")
[http://ubuntuforums.org/showthread.php?t=680690]("http://ubuntuforums.org/showthread.php?t=680690")

---

### Post by jonasa on 2008-04-13
I have solved the dependency - kind of:
I found that after installing Octave without getting a working version and a dependency problem I uninstalled it.

For some reason one part of the Octave installation remained, making the dependency problem remain.

By starting "Synaptic Package manager" and searching for "All installed packages" I found that there was a part remaining in the octave installation. I marked it and checked "remove completely" 

Atfer this it was possible to run
sudo apt-get install -f
without errors.


But:
When I once again choose to install Octave 2.9 using the Synaptic Package Manager I get and installation error:

E: /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb: trying to overwrite `/usr/lib/libamd.so.1', which is also in package libumfpack4

Very similar error to the one before.

If I run
jonasa@slowfox:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsuitesparse
The following NEW packages will be installed:
  libsuitesparse
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/898kB of archives.
After unpacking 2179kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 123560 files and directories currently installed.)
Unpacking libsuitesparse (from .../libsuitesparse_3.0.0-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libamd.so.1', which is also in package libumfpack4
Errors were encountered while processing:
 /var/cache/apt/archives/libsuitesparse_3.0.0-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jonasa@slowfox:~$ 

I get exactly the same error as before. It seems that Synaptic fails to install libsuitesparse


Well, I seem not be able to get octave to run - but at least I have a working system that can be updated. Partial success!!

/Jonas

---

### Post by gaoyicn on 2008-04-16
I got the same problem, I would *guess* that the problem lies in both two packages:
suitesparse and umfpack
will need to install libamd.* which cause the confliction.

What I'm doing now is to install libsuitesparse(including libsuitesparse-dev since I'm trying to compile octave from source) and completely uninstall the umfpack.

Now the ./configure step of octave is working fine and it compiles.

Now it finishes compiling and it works.

---

