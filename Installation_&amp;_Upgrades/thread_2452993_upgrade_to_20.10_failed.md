---
title: "upgrade to 20.10 failed?"
date: 2020-11-01
forum: Installation &amp; Upgrades
---

### Post by LMH1 on 2020-11-01
> 
[FONT=monospace][COLOR=#000000]apt_pkg.Error: E:Could not configure 'libc6:amd64'. , E:Klarte ikke gjennomføre umiddelbar konfigurasjon av «[/COLOR]
libnss-nis:amd64». Se man 5 apt.conf under APT::Immediate-Configure for detaljer. (2) 
Error in sys.excepthook: 
Traceback (most recent call last): 
  File "/usr/lib/python3/dist-packages/problem_report.py", line 477, in add_to_existing 
    self.write(f) 
  File "/usr/lib/python3/dist-packages/problem_report.py", line 430, in write 
    block = f.read(1048576) 
  File "/usr/lib/python3.8/codecs.py", line 322, in decode 
    (result, consumed) = self._buffer_decode(data, self.errors, final) 
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8b in position 1: invalid start byte 

Original exception was: 
apt_pkg.Error: E:Could not configure 'libc6:amd64'. , E:Klarte ikke gjennomføre umiddelbar konfigurasjon av «
libnss-nis:amd64». Se man 5 apt.conf under APT::Immediate-Configure for detaljer. (2) 
Error in function: install 

apt_pkg.Error: E:Klarte ikke gjennomføre umiddelbar konfigurasjon av «libffi8ubuntu1:amd64». Se man 5 apt.con
f under APT::Immediate-Configure for detaljer. (2) 
Error in sys.excepthook: 
Traceback (most recent call last): 
  File "/usr/lib/python3/dist-packages/problem_report.py", line 477, in add_to_existing 
    self.write(f) 
  File "/usr/lib/python3/dist-packages/problem_report.py", line 430, in write 
    block = f.read(1048576) 
  File "/usr/lib/python3.8/codecs.py", line 322, in decode 
    (result, consumed) = self._buffer_decode(data, self.errors, final) 
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8b in position 1: invalid start byte 

Original exception was: 
apt_pkg.Error: E:Klarte ikke gjennomføre umiddelbar konfigurasjon av «libffi8ubuntu1:amd64». Se man 5 apt.con
f under APT::Immediate-Configure for detaljer. (2) 

Upgrade infeasible  

The upgrade could not be completed, there were errors during the  
upgrade process.  
[/FONT]

So did someone get that issue? how to fix it?

---

### Post by yapidumoac on 2020-11-02
[LEFT][COLOR=#333333][FONT=monospace][[LEFT][COLOR=#333333][FONT=monospace]Found a workaround[/FONT][/COLOR][/LEFT]]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1899272")

&#8220;Found a workaround, but beware here be dragons and this could kill your OS install!

Do not do this unless you know what you are doing!
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]After do-release-upgrade -d fails
cd /var/cache/apt
sudo dpkg --force-depends --force-breaks -i libnss-nis_3.1-0ubuntu4_amd64.deb[/FONT][/COLOR][COLOR=#333333][FONT=monospace]This will install the package that fails regardless missing deps and the possibility of breaking glibc.
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]Try upgrading again
sudo do-release-upgrade -d
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]This worked for me.&#8221;
[/FONT][/COLOR][/LEFT]

---

### Post by LMH1 on 2020-11-02
Sorry its did not works: [FONT=monospace][COLOR=#54ff54]**larsmartin@Multicom-laptop**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/var/cache/apt**[/COLOR][COLOR=#000000]$[/COLOR]
[/FONT]
> [FONT=monospace][COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#ff5454]**error:**[/COLOR][COLOR=#000000] cannot access archive 'libnss-nis_3.1-0ubuntu4_amd64.deb':[/COLOR]
[/FONT]

> [FONT=monospace][COLOR=#000000]sudo do-release-upgrade -d [/COLOR]
Checking for a new Ubuntu release 
Upgrades to the development release are only  
available from the latest supported release.
[/FONT]

Its works to upgrade 2 computer so need to find why this is so much high? did you know error with nvidia card and 20.10 that give only 1024x786 screensize?

---

### Post by grahammechanical on 2020-11-03
This command will upgrade to the development release

```
sudo do-release-upgrade -d
```

It is the d switch ( -d ) that does it. So, if you run that command on Ubuntu 20.10 you will upgrade to Ubuntu 21.04 development version. If you are on Ubuntu 20.04 that command will not work because 20.10 is no longer the development version. For that command to work you have to be on the latest supported release which is 20.10. Try running the command without the d switch ( -d )

Regards

---

### Post by LMH1 on 2020-11-03
Yes but i get isssue longer up so how to fix?
Or its only way to reinstall and try again?

Or did you have information how to find out why its only happed on one computer?
I know XFCE desktop may give issue with upgrade but did not know why? Its it other thing that know issue with upgrade?

---

