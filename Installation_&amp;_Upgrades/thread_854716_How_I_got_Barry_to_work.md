---
title: "How I got Barry to work"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by thieves.honor on 2008-07-09
Here are the steps that I have used to get barry to work successfully on two different machines and one virtual machine.  The virtual machine is running ubuntu 8.04 32bit system while the two live machines are running ubuntu 8.04 server 64 and ubuntu 8.04 desktop 64.

Download [barry_0.12.tar.bz2]("http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564&release_id=586115") from the barry sourceforge page.
Download [msynctool-0.22.tar.bz2]("http://www.opensync.org/download/releases/0.22/") from the opensync 0.22 download page.

Install the following packages from the ubuntu repositories. (I'm not sure if you have to have backports and multiverse enabled)

sudo apt-get update
sudo apt-get install opensyncutils libopensync-dev opensync-plugin-* libusb-dev libssl-dev libboost-serialization-dev libtar-dev libgtkmm-2.4-dev libglademm-2.4-dev libevolution3.0-cil doxygen doxygen-gui g++ gawk gcc-avr libgcj8-dev g77

untar both msynctool and barry into their own directories.
go into the msynctool directory and build it.

./configure
make
sudo make install

go into the barry direction and built it

./configure --with-boost=/usr --enable-gui --enable-opensync-plugin
make
sudo make install

barry and msynctool are now both compiled and installed.  at this point if I plugged by blackberry in and ran bcharge, I would get an error message.  To fix this i had to run ldconfig.

after running that I got a different error:
  Usb::Error caught: (-1, error sending control message: Operation not permitted): Probe: GetConfiguration failed
my understanding is that this is because there is not a udev rule for the blackberry device.  To fix this there is a udev directory within the source folder.

sudo cp udev/10-blackberry-rules.Debian /etc/udev/rules.d/10-blackberry.rules

restart the udev service

sudo /etc/init.d/udev restart

you should be able to run bcharge and btool without any issues.

to setup msynctool to sync with evolution follow the following steps;

run barrybackup and write down your device pin
msynctool --addgroup BB
msynctool --addmember BB barry-sync
msynctool --addmember BB evo2-sync
msynctool --configure BB 1
replace default with your device pin

to sync run msynctool --sync BB
This will only sync your contacts and calendar.  if anyone has a way to sync memo and tasks please let me know.

I got most of my info from theses sites.  they are worth taking a look at.
[http://www.netdirect.ca/software/packages/barry/install.php](http://www.netdirect.ca/software/packages/barry/install.php)
[http://www.linux.com/feature/123251](http://www.linux.com/feature/123251)

---

### Post by apc15x on 2008-07-23
Thank you for this great post but I am almost finish and I am running into a problem. I am not sure if it is me because of lack of knowledge or what but this is my problem. I get to this point: [HTML]after running that I got a different error:
Usb::Error caught: (-1, error sending control message: Operation not permitted): Probe: GetConfiguration failed
my understanding is that this is because there is not a udev rule for the blackberry device. To fix this there is a udev directory within the source folder.
[/HTML]I then change my directory to ~/barry-0.12/udev$ then I run the script [HTML]sudo cp udev/10-blackberry-rules.Debian /etc/udev/rules.d/10-blackberry.rules
[/HTML]and this is what I get: cp: cannot stat `udev/10-blackberry-rules.Debian': No such file or directory
Now is it me or is there another problem? Any help would be appreciated.:mad:

---

### Post by zippypickle on 2008-07-23
I received the same error.  But the The udev file is named slightly different.  Instead of '10-blackberry-rules.Debian', there's a period between blackberry and rules, instead of the dash...  Look in your barry udev rules folder for the exact name of the file you are copying.

I entered the blackberry rules folder and this worked for me:

sudo cp 10-blackberry.rules.Debian /etc/udev/rules.d/10-blackberry.rules

---

### Post by apc15x on 2008-07-24
Thanks for the reply zippypickle, I think that it worked but now I have not figured out how to save the PIN number into the Terminal. Looks like this is going to take me one step at a time before I am finished. Again any help would be appreciated.

---

### Post by wolf4914 on 2008-10-16
I installed all the stuff mentioned on 8.10 beta and I get this error
/barry# ./buildgen.sh cleanall
make: *** No rule to make target `distclean'.  Stop.
make: *** No rule to make target `distclean'.  Stop.
make: *** No./buildgen.sh rule to make target `distclean'.  Stop.


   I have version 0.14 that I extracted
  Just ./buildgen.sh spits this out:
./buildgen.sh: 62: aclocal: not found

---

### Post by supremedalek on 2008-11-06
It seems that aclocal comes in the automake package. After installing it, I get the following:

```
raub@monaco:~/todo/barry/barry-0.14$ ./buildgen.sh 
./buildgen.sh: 62: libtoolize: not found
./buildgen.sh: 62: libtoolize: not found
./buildgen.sh: 62: libtoolize: not found
raub@monaco:~/todo/barry/barry-0.14$ 
```

Now, libtoolize is part of libtool, so I installed it too. And, that seems to have done the trick... at least up to this point. 

I hope this helps!

---

### Post by wolf4914 on 2008-12-07
> **wolf4914 said:**
> I installed all the stuff mentioned on 8.10 beta and I get this error
/barry# ./buildgen.sh cleanall
make: *** No rule to make target `distclean'.  Stop.
make: *** No rule to make target `distclean'.  Stop.
make: *** No./buildgen.sh rule to make target `distclean'.  Stop.


   I have version 0.14 that I extracted
  Just ./buildgen.sh spits this out:
./buildgen.sh: 62: aclocal: not found

   Some time later I installed barry debs for 64 bit from here: [http://download.opensuse.org/repositories/home:/ndprojects/Ubuntu804/amd64/](http://download.opensuse.org/repositories/home:/ndprojects/Ubuntu804/amd64/)  and all works fine ! It was the last reason to ever boot in windoze or MAC to charge/sync my 8830/:D

---

### Post by BenFischer on 2008-12-28
I'm unable to configure msynctool right now.  I downloaded version .22, and extracted it to my Downloads folder in home directory.  Does it need to be somewhere else to access the dependencies? 
I keep getting 
No package 'opensync-1.0' found
No package 'osengine-1.0' found
I even tried downloading OpenSync and extracting it to my downloads folder, but I couldn't configure it either because it couldn't access some dependencies (which I also put in the downloads folder).  Therefore I'm thinking that these things should be put somewhere else like etc/.... Yes, No, other ideas?
Thanks,
Ben

---

### Post by jwrede on 2008-12-30
I'm having a similar problem.  I followed the steps outlined above and everything worked when I omitted the --enable-opensync-plugin, but when I tried to run through it again with that flag set, I get this:
```
checking for PACKAGE... configure: error: Package requirements (opensync-1.0 glib-2.0) were not met:

No package 'opensync-1.0' found

```

I've Googled this error and found a few posts citing this error with both Barry and MultiSync, but none of them had a resolution.  Any help would be great!

Thanks,
Johann

---

### Post by tamccain on 2009-01-06
does anyone know how to get Barry to sync repeating appointments???

So far I can't find anything.

---

### Post by go_beep_yourself on 2009-03-10
How do you get the Blackberry to work as a modem?

---

### Post by version7x on 2009-04-03
> **BenFischer said:**
> I'm unable to configure msynctool right now.  I downloaded version .22, and extracted it to my Downloads folder in home directory.  Does it need to be somewhere else to access the dependencies? 
I keep getting 
No package 'opensync-1.0' found
No package 'osengine-1.0' found
I even tried downloading OpenSync and extracting it to my downloads folder, but I couldn't configure it either because it couldn't access some dependencies (which I also put in the downloads folder).  Therefore I'm thinking that these things should be put somewhere else like etc/.... Yes, No, other ideas?
Thanks,
Ben

Hopefully, you've figured this out by now... but if not,  download and install libopensync... same site and steps as msynctool.  Once i did the config/make/makeinstall dance with libopensync, those package errors went away for me!

I'm still struggling with the system seeing my device:

```
btool
Blackberry devices found:
No device selected

```

and the evo2-sync plugin:
```
 msynctool --addmember BB evo2-sync
Unable to instance plugin with name evo2-sync: Unable to find the plugin "evo2-sync"

```

---

### Post by P Minix on 2009-04-15
> **version7x said:**
> Hopefully, you've figured this out by now... but if not,  download and install libopensync... same site and steps as msynctool.  Once i did the config/make/makeinstall dance with libopensync, those package errors went away for me!

At this step I am recieving sqlite3 dependency errors.

[INDENT]checking for PACKAGE... configure: error: Package requirements (glib-2.0 gmodule-2.0 gobject-2.0 gthread-2.0 sqlite3) were not met:

No package 'sqlite3' found[/INDENT]

-- of course sqlite3 is installed

[INDENT]sudo apt-get install sqlite3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sqlite3 is already the newest version.
[/INDENT]

Any ideas?

---

### Post by P Minix on 2009-04-17
OK,  had to download the tarball into my home directory for sqlite3 and install manually.  The .deb archive didnt work.

Then libopensync compiles and installs. Onto Msync - and same error

```
[INDENT]checking for PACKAGE... configure: error: Package requirements (glib-2.0 opensync-1.0 osengine-1.0) were not met:

No package 'opensync-1.0' found
No package 'osengine-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/INDENT]
```

Thought I would give barry a shot anyway.  No joy, configures clean but make produces a litany of errors:

```
[INDENT]time.cc:107: warning: deprecated conversion from string constant to 'char*' 
.... and .... 
data.cc: In function 'bool Barry::IsHexData(const std::string&)':
data.cc:47: error: 'strchr' was not declared in this scope
data.cc: In constructor 'Barry::Data::Data()':
data.cc:72: error: 'memset' was not declared in this scope
data.cc: In constructor 'Barry::Data::Data(int, size_t)':
data.cc:83: error: 'memset' was not declared in this scope
data.cc: In copy constructor 'Barry::Data::Data(const Barry::Data&)':
data.cc:106: error: 'memcpy' was not declared in this scope
data.cc: In member function 'void Barry::Data::MakeSpace(size_t)':
data.cc:119: error: 'memcpy' was not declared in this scope
data.cc:120: error: 'memset' was not declared in this scope
data.cc: In member function 'void Barry::Data::CopyOnWrite(size_t)':
data.cc:135: error: 'memcpy' was not declared in this scope
data.cc: In member function 'void Barry::Data::Zap()':
data.cc:264: error: 'memset' was not declared in this scope
data.cc: In member function 'Barry::Data& Barry::Data::operator=(const Barry::Data&)':
data.cc:275: error: 'memcpy' was not declared in this scope
data.cc: In function 'bool Barry::IsEndpointStart(const std::string&, int&)':
data.cc:389: error: 'strncmp' was not declared in this scope
data.cc:392: error: 'atoi' was not declared in this scope
make[2]: *** [data.lo] Error 1
make[2]: Leaving directory `/home/pat/barry-0.12/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/pat/barry-0.12'
make: *** [all] Error 2[/INDENT]
```

So I gave it try with Barry-0.14 and it builds with no errors.  Have to get back to real job now and will continue over the weekend, but this has got to be easier.  I have many good reasons for converting several users to Ubuntu - but this BlackBerry issue is a show stopper.

One question, should we be doing this in some specific directory, rather then HOME?

Second question, with regards to this forum - the only way I could get this to post was to use the "code" tags around the console text captures, other wise I flagged for having too many "images" in my post.  Am I doing something wrong?

---

### Post by P Minix on 2009-04-17
Let me qualify that: barry 0.14 configures clean with boost and gui enabled, does not with opensync enabled.  Looks like opensync is the problem.  Miller time, so nothing more for now.

---

### Post by P Minix on 2009-04-20
Is there anyone trying to clean this up for Ubuntu.  Other then a true Exchange client, this is probably the biggest hurdle for Ubuntu's use as an alternative desktop.

---

### Post by P Minix on 2009-04-21
Got past the opensyn-1.0 missing error by installing the entire MultiSync .90 tree using Synaptic.  I'm not sure which file I was missing, but will go back on a clean machine and try it systematically.

MSync 22 and Barry 0.14 configure/make/install clean

Modified and restarted udev; then failure

[INDENT]pat@pat:~/barry-0.14$ sudo /etc/init.d/udev restart
 * Loading additional hardware drivers...                                                                          [ OK ] 
pat@pat:~/barry-0.14$ bcharge
Scanning for Blackberry devices...
pat@pat:~/barry-0.14$ btool
btool: error while loading shared libraries: libbarry.so.0: cannot open shared object file: No such file or directory
pat@pat:~/barry-0.14$ 
[/INDENT]

I will get back to this later.  Barry should really be a plugin under MSync, any thoughts.

---

### Post by zero7404 on 2009-04-29
i'd like a tool like this that works well under 8.10....
i tried installing it once, but got issues @ the make command....

all i'd really need it for is backup/restore of files, charge the phone and the ability to install a new OS on the phone would be nice....

---

### Post by phorgan1 on 2009-06-29
I'm still getting 

> Usb::Error caught: (-1, error sending control message: Operation not permitted): Probe: GetConfiguration failed

even though I did:
> sudo cp udev/debian/10-blackberry.rules /etc/udev/rules.d

and restarted udev (and even later restarted the machine.

Everything works fine as root.  Any ideas?

---

### Post by ozzyprv on 2009-07-08
> **phorgan1 said:**
> I'm still getting 


even though I did:

and restarted udev (and even later restarted the machine.

Everything works fine as root.  Any ideas?


Same here. I installed Barry from APP.

---

### Post by skrap on 2009-09-09
I am trying to ./configure barry and this is what I am getting.

./configure: line 1843: syntax error near unexpected token `dist-bzip2'
./configure: line 1843: `AM_INIT_AUTOMAKE(dist-bzip2)'

Any ideas would be appreciated.

Jaunty on a AMD 64 processor 2gb RAM 320gb hd

---

### Post by marcottebj on 2010-07-20
I was still getting the "Operation not Permitted Error" after following these instructions and copying the 10-blackberry.rules.Debian over the correct directory.  
 
It took some research, but I found the solution to the problem, and I thought others might benefit as well (since this thread kept coming up in my google searches)
 
1.  open a terminal window
2.  type btool -M (you should get the operation not permitted error if you're having this problem)
3.  type the command "lsusb" to get a listing of all usb devices plugged into your system
4.  Find the one listed as Research In Motion and write down everything you see listed for that device
5.  in the terminal, enter "gedit /etc/udev/rules.d/10-blackberry.rules" (without quotes)
6.  Here, I copied the top two entries (four lines) under newer devices with USB storage
7.  I pasted what I had copied at the bottom of that page, and verified (or modified) the part in both entries:  SYSFS{idVendor}=="ofca"  (ofca should represent first part of the ID from the lsusb command that you wrote down)
8.  Next I modified the part of the script (both entries): SYSFS{idProduct}=="0004"  (in my case I had to change it to SYSFS{idProduct}=="0008"  (the number should correspond to the last part of the ID right of the colon from the LSUSB command that you wrote down)
9.  Save the file
10.  Reboot the udev service (or just restart your machine)
 
In my case everything worked, and I did not have any further permission issues.  The blackberry device syncs perfectly every time.

---

### Post by marcottebj on 2010-07-20
Also, I found this article which seemed to have the best set of instructions for getting Barry to work: [http://www.linux.com/news/embedded-mobile/mids/8210-syncing-your-blackberry-on-linux](http://www.linux.com/news/embedded-mobile/mids/8210-syncing-your-blackberry-on-linux)

---

### Post by zevans on 2011-07-17
I have the permissions problem too, using barry 0.17 on Maverick.

There are .deb packages here:

[URL="http://sourceforge.net/projects/barry/files/barry/barry-0.17.1/ubuntu1004/"]http://sourceforge.net/projects/barry/files/barry/barry-0.17.1/ubuntu1004/
[/URL]```
Usb::Error caught: (-1, error sending control message: Operation not permitted): Probe: GetConfiguration failed

```

The packages include udev rules and they definitely include ```
0fca:8004
``` - the ID for my Curve.

And guess what - it works for root but not for my username. So I guess there's something wrong with
```
# 99-blackberry-perms.rules
ATTRS{idVendor}=="0fca", ATTRS{idProduct}=="8004", GROUP="plugdev", MODE="0664"

```

---

### Post by zevans on 2011-07-17
As usual, as soon as you post about it you realise the problem is obvious...

I added my user to the "plugdev" group and it works!

---

