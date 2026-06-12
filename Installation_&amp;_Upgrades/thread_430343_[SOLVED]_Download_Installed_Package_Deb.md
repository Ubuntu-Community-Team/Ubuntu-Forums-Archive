---
title: "[SOLVED] Download Installed Package Deb"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by prince_niceguy on 2007-05-02
By mistake run the command to sudo apt-get clean and it deleted all the files in the archive folder. 

Is there a way by which I can download these files back without reinstallation of the packages?

I know I can do a sudo apt-get install -d [package name] but I am not able to get the list of all the packages installed on my comp.

any help in getting this done would be really helpful.

Thanks

---

### Post by prince_niceguy on 2007-06-06
bump....

---

### Post by christhemonkey on 2007-06-06
EDIT: This doesnt work, il come back to you!

```
sudo su
apt-cache pkgnames > apt-get -d
exit
```

Something like that?

Where "apt-get -d" downloads the package files only and "apt-cache pkgnames" lists all packages installed on a system.


This might not work though as its just off the top of my head :D

---

### Post by prince_niceguy on 2007-06-06
great... thanks for how to list down the packages... i copied all to kwrite and then appended with suo apt-get -d... the option -d is not working in the redirection mode like you stated.. not sure why... 

thanks mate...

---

### Post by christhemonkey on 2007-06-06
The way to do it would be:
```
sudo apt-get install -d --reinstall PACKAGENAME 
```

But i cant get it to accept all the package names installed on a system for some reason....

---

### Post by christhemonkey on 2007-06-06
Ok couldnt think of a way to it in bash so wrote you a little script in python.

Run it like this:
```
sudo python helpguy.py 
```
(you need to be in the directory you downloaded it to though)
```
cd ~/Desktop 
```

It will take a while as it has to download a *lot* of stuff.
Enjoy!

---

### Post by christhemonkey on 2007-06-06
Oh and that script will fall over if it tries to get something from an unverified repository
(ie wines repo and others without a valid GPG key)

Can try making it skip those files....

---

### Post by christhemonkey on 2007-06-06
Ok now it includes error handling (such as the file not being on server, or file not being verified)


Run it same way as before.
Enjoy!

---

### Post by prince_niceguy on 2007-06-06
thanks mate... the script worked...

I had to install python-pexpect from repository to run the script... now it is working great... downloading all the software... i want to take it to CD and put on a comp not connected to net...

thanks a ton...

---

### Post by christhemonkey on 2007-06-07
You can also use another program i have written to download packages for that offline pc.

Say if u dont want to install them on your online ubuntu pc.
Also made a .exe of it so you can run it on windows.

See here:
[http://ubuntuforums.org/showthread.php?p=2742822#post2742822](http://ubuntuforums.org/showthread.php?p=2742822#post2742822)

Another mirror further up the page if that is down.
You will need (if you want to run it under linux) the .py file and the .glade file. (and i might need to upload a revision but yeah we'll see!)
Enjoy!

EDIT:
Direct Links for you, cos im nice!
[http://software.chrisbeagles.ath.cx/wubdependsv4/Source/wubdepends3.py](http://software.chrisbeagles.ath.cx/wubdependsv4/Source/wubdepends3.py)
[http://software.chrisbeagles.ath.cx/wubdependsv4/Source/wubdep.glade](http://software.chrisbeagles.ath.cx/wubdependsv4/Source/wubdep.glade)

Download them both then run the python script.
Sorted!

---

### Post by lospo on 2008-07-18
I've got this strange output, could it be because my ubuntubox is localized in ITALIAN????

[PHP]
acl
Traceback (most recent call last):
  File "helpguy.py", line 13, in <module>
    index = child.expect(["Do you want to continue [Y/n]?", "Download complete and in download only mode", "Install these packages without verification [y/N]?"])
  File "/usr/lib/python2.5/site-packages/pexpect.py", line 1064, in expect
    return self.expect_list(compiled_pattern_list, timeout, searchwindowsize)
  File "/usr/lib/python2.5/site-packages/pexpect.py", line 1143, in expect_list
    raise TIMEOUT (str(e) + '\n' + str(self))
pexpect.TIMEOUT: Timeout exceeded in read_nonblocking().
<pexpect.spawn object at 0x86e990>
version: 2.1 ($Revision: 395 $)
command: /usr/bin/apt-get
args: ['/usr/bin/apt-get', 'install', '--reinstall', '-d', 'acl']
patterns:
    Do you want to continue [Y/n]?
    Download complete and in download only mode
    Install these packages without verification [y/N]?
buffer (last 100 chars): 
before (last 100 chars): kB di archivi. 
Dopo questa operazione verranno occupati 0B di spazio su disco.
Continuare [S/n]? 
after: <class 'pexpect.TIMEOUT'>
match: None
match_index: None
exitstatus: None
flag_eof: False
pid: 27801
child_fd: 3
closed: False
timeout: 30
delimiter: <class 'pexpect.EOF'>
logfile: None
maxread: 2000
ignorecase: False
searchwindowsize: None
delaybeforesend: 0.1
delayafterclose: 0.1
delayafterterminate: 0.1

[/PHP]

Is this right?

---

### Post by lospo on 2008-07-19
Yes, it was the language, simply change it to english at the loging script and everything work.

---

