---
title: "Problem with skype-python"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by hissou86 on 2010-12-03
Hi averybody,
i am new in ubuntu forums but i like it so much.

to begin :
i always face when installing some programs or updatings, i face this issue:
---
update-python-modules: error: /usr/share/python-support/python-skype.public is not a directory
dpkg: error processing python-skype (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python-skype
E: Sub-process /usr/bin/dpkg returned an error code (1)
------
wich deals, as you see, with skype-python.
I've faced this problem even when i wanted to install java-common


thank u in advance

---

### Post by sikander3786 on 2010-12-03
Welcome to the forums :-)

Try these command from Applications > Accessories > Terminal and post the output.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by hissou86 on 2010-12-03
> **sikander3786 said:**
> Welcome to the forums :-)

Try these command from Applications > Accessories > Terminal and post the output.

```
sudo apt-get install -f
```
----
Output :
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdvbpsi4 libxosd2 libvlc0 vlc-nox libdvdnav4 libiso9660-5 vlc-plugin-pulse
  libmodplug0c2 libtar libvcdinfo0 libebml0 libmpcdec3 libmatroska0
  libsdl-image1.2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python-skype (1.0.31.0-1) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/python-skype.public is not a directory
dpkg: error processing python-skype (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python-skype
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
```
sudo dpkg --configure -a
```
Output:
```
Nothing
```


Thanks for your help

---

### Post by sikander3786 on 2010-12-03
What if you try removing and purging that package.

```
sudo apt-get remove --purge python-skype
```

---

### Post by hissou86 on 2010-12-03
The problem persist and the same output.

---

### Post by sikander3786 on 2010-12-03
Follow this post and replace 'tzdata-java' with 'python-skype'.

[http://ubuntuforums.org/showpost.php?p=10127988&postcount=9](http://ubuntuforums.org/showpost.php?p=10127988&postcount=9)

---

### Post by hissou86 on 2010-12-03
When i typed :
```
sudo apt-get update
```
I got :
```
Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/Release.gpg  Could not resolve 'download.skype.com'

```

i have to note that i am connecting via a proxy, do you think that the problem is due to that?

Thanks

---

### Post by sikander3786 on 2010-12-03
Means the original message is gone?

Regarding the new error, pleae post the output of this one.

```
cat /etc/apt/sources.list
```

---

### Post by hissou86 on 2010-12-03
Yes, the original message is gone.
```
cat /etc/apt/sources.list

```
Output:
```

#deb http://apt.wicd.net/ jaunty extras
#deb http://www.backports.org/debian lenny-backports main contrib non-free
deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype


```

What does that mean please?

---

### Post by sikander3786 on 2010-12-03
Means you are back in business :-)

Edit your sources.list by,

```
gksudo gedit /etc/apt/sources.list
```

Comment these 2 lines with # in the beginning.

```
deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
```

So that they look like,

```
#deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
#deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype
```

Save and close and now,

```
sudo apt-get update
```

There should be no more errors any more :-)

---

### Post by hissou86 on 2010-12-03
Sorry ...
there is yet an error.
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```

thanks

---

### Post by sikander3786 on 2010-12-03
We will hopefully deal with this one as well :-)

```
gksudo gedit /etc/apt/apt.conf
```

Hopefully, it would be an empty file (newly created). Put this lines in there. (If it is not empty, paste these lines at the bottom of the file in a new line)

```
APT::Cache-Limit "42123456";
```

Save and close. Run apt-get update again. Another error regarding dpkg/status is expected here. Be patient and post that one as well :-)

---

### Post by hissou86 on 2010-12-06
The same error appears :

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

```

Thanks a lot

---

### Post by sikander3786 on 2010-12-06
Try to use an older dpkg/status file.

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
```

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

```
sudo apt-get update
```

---

### Post by hissou86 on 2010-12-06
This is the result :
```
Reading package lists... Done

```

Thanks

---

### Post by sikander3786 on 2010-12-06
> **hissou86 said:**
> This is the result :
```
Reading package lists... Done

```

Thanks
Glad to know it is all sorted out. This was a long one for me at least :P

You can now mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

