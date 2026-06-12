---
title: "How to get Python back after accidentally removing it"
date: 2016-10-28
forum: Installation &amp; Upgrades
---

### Post by jeevansai2 on 2016-10-28
I was trying to update my Software Center, but unfortunately removed  it. Meanwhile I removed python and many python related files from my  system unknowingly. Now if I am trying to install other software using  apt-get, the following package errors are encountered. I am unable to  remove or configure. Every time it says dependency errors prevent me  from doing so.
  complete error:  [http://pastebin.com/cMDsAJmE](http://pastebin.com/cMDsAJmE)

---

### Post by oldfred on 2016-10-28
You never ever uninstall python. You should have seen a very long list of dependencies that also were uninstalled. Or most of desktop.

It used to be the only fix was either a total reinstall & restore from backup, or chroot and in effect reinstall system from that. Then network connection also depended on python.

You should be able just to totally reinstall desktop. Which desktop are you running?
If standard Ubuntu:
 sudo apt-get install ubuntu-desktop

---

### Post by ian-weisser on 2016-10-28
apt uses Python. If have uninstalled python, apt and apt-get and all other programs that use apt (like Synaptic and Software Center) won't work.
In theory, you can download (somehow) and then install the python package(s) using dpkg.

However, oldfred is right - repair is probably not worthwhile. Backup your data using a LiveUSB and then reinstall.

---

### Post by jeevansai2 on 2016-10-29
can i install all error packages by downloading them if so can you explain how

---

### Post by ian-weisser on 2016-10-29
There are a couple prerequisite skills you must be proficent in *before* starting upon the odyssey you have chosen:
- Manually downloading a package from packages.ubuntu.com. 
- Reading error messages.
- Locating and reading logfiles in /var/log/apt

None of these skills is particularly hard on a fully-functioning machine.
They are real linux-maintenance skills, like other household skills (truing a bicycle wheel, fixing a faucet drip).
The repair, if it works, will take time. A few days. Perhaps a week.

First step: Please show us the record in your apt log showing what packages were deleted. Not your entire apt log. Just the relevent entries.

---

### Post by jeevansai2 on 2016-10-29
python-jwt
  python-oauthlib
  python-zope.interface
  python-attr
  python-service-identity
  python-twisted-core
  python-twisted-web
  python-ubuntu-sso-client
  ubuntu-sso-client
  python-bzrlib
  bzr
  gimp
  python-sip
  git-cola
  gtk-recordmydesktop
  libglib2.0-dev
  meld
  mgltools-bhtree
  mgltools-sff
  python-zsi
  mgltools-mglutil
  python-appindicator
  python-apt
  python-six
  python-snappy
  python-twisted
  python-txaio
  python-autobahn
  python-bs4
  python-characteristic
  python-distro-info
  python-ecdsa
  python-gpgme
  python-html5lib
  python-lazr.restfulclient
  python-launchpadlib
  python-mysql.connector
  python-ndg-httpsclient
  python-opengl
  python-pexpect
  python-pip
  python-secretstorage
  python-serial
  python-setuptools
  python-ubuntutools
  python-urllib3
  python-vtk6
  python-wheel
  python-xapian
  python-xdg
  python-piston-mini-client

and some others which are reinstalled using apt-get install -f but these are not getting installed in any way

---

### Post by ian-weisser on 2016-10-29
Please show us the complete output of trying to reinstall using apt, including the command you used.

What release of Ubuntu are you using? 12.04? 14.04? 16.04? 16.10?

Please elaborate: Why, exactly, were you 'trying to update Software Center'?

---

### Post by jeevansai2 on 2016-10-29
[http://pastebin.com/cMDsAJmE](http://pastebin.com/cMDsAJmE) here it is.my ubuntu version is 16.10 my software center is not working so i tried to update but i removed python with apt unknowingly.

---

### Post by ian-weisser on 2016-10-29
Clearly Python2 and Python3 seem to be installed, so saying 'I removed python' seems misleading.
Or do your logs indicate actual removal? If so, please show us that log entry. That would help a lot...

Try 'sudo apt install --reinstall python-jwt' (the first package error) and please show us the complete output.

---

### Post by jeevansai2 on 2016-10-29
[http://pastebin.com/UR8atbjA](http://pastebin.com/UR8atbjA)  even synaptic shows i have broken packages but it was not able to correct them

---

### Post by ian-weisser on 2016-10-29
> [COLOR=#333333]Preparing to unpack .../python-jwt_1.3.0-1_all.deb ...
[/COLOR][COLOR=#333333]/var/lib/dpkg/info/python-jwt.prerm: 6: /var/lib/dpkg/info/python-jwt.prerm: [/COLOR][B]pyclean: not found
[/B][COLOR=#333333]dpkg: warning: subprocess old pre-removal script returned error exit status 127

[/COLOR][COLOR=#333333]dpkg: trying script from the new package instead ...
[/COLOR][COLOR=#333333]/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: [/COLOR][B]pyclean: not found

[/B][COLOR=#333333]dpkg: error processing archive /var/cache/apt/archives/python-jwt_1.3.0-1_all.deb (--unpack):
[/COLOR][COLOR=#333333]subprocess new pre-removal script returned error exit status 127
[/COLOR][COLOR=#333333]/var/lib/dpkg/info/python-jwt.postinst: 6: /var/lib/dpkg/info/python-jwt.postinst: [/COLOR]**pycompile: not found**

pyclean and pycompile are included in the python-minimal package. Try installing or re-installing python-minimal and python3-minimal

It's slow, but it's progress.

---

