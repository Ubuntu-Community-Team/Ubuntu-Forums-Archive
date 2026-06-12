---
title: "dpkg: error processing ttf-mscorefonts-installer"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by negacy on 2009-11-25
Hello,
I was looking to install media player for firefox in ubuntu 9.04 and suddenly I stuck the following error. Now I can't install any package, pls help
```


**sudo apt-get -f install**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (2.6) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-11-25 11:40:42--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Giving up.


........


--2009-11-25 11:41:52--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Giving up.

andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)




```

---

### Post by dddanmar on 2009-11-25
I can view that from here, what happens if you visit 
[http://switch.dl.sourceforge.net/sourceforge/corefonts/](http://switch.dl.sourceforge.net/sourceforge/corefonts/)
in your webbrowser? It works fine for me here so it should work. 
If not, can you ping it in the terminal?

Or, download the files from a sourceforge mirror if switch.dl doesn't want to talk to you and look for where they need to go.

---

### Post by atomizer on 2009-11-25
Is a bug, [see post 21 of this bugreport for solution]("https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217")

---

### Post by negacy on 2009-11-25
@[dddanmar]("http://ubuntuforums.org/member.php?u=960893"): I think I should have posted the whole error msg. When I visit [http://switch.dl.sourceforge.net/sourceforge/corefonts/](http://switch.dl.sourceforge.net/sourceforge/corefonts/) I can see their site and asking me if I want to download but that is not the only site I am looking for. Anyway, the whole error msg is 
```

&#9492;&#9472;(21:54 $)&#9472;> sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  google-chrome-unstable
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 49.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 184616 files and directories currently installed.)
Removing google-chrome-unstable ...
Processing triggers for man-db ...
Setting up ttf-mscorefonts-installer (2.6) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-11-25 21:54:44--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Giving up.

--2009-11-25 21:54:49--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... failed: Connection timed out.
Giving up.

--2009-11-25 21:54:55--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... 194.95.236.6
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... failed: Connection timed out.
Giving up.

--2009-11-25 21:55:01--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... failed: Connection timed out.
Giving up.

--2009-11-25 21:55:06--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... failed: Connection timed out.
Giving up.

--2009-11-25 21:55:11--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... 211.79.60.17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Giving up.

--2009-11-25 21:55:16--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... failed: Connection timed out.
Giving up.

--2009-11-25 21:55:29--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... failed: Connection timed out.
Giving up.

--2009-11-25 21:55:35--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... failed: Connection timed out.
Giving up.

--2009-11-25 21:55:40--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... 72.26.192.194
Connecting to voxel.dl.sourceforge.net|72.26.192.194|:80... failed: Connection timed out.
Giving up.

--2009-11-25 21:55:46--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... failed: Connection timed out.
Giving up.

--2009-11-25 21:55:51--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... failed: Connection timed out.
Giving up.

--2009-11-25 21:55:57--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Giving up.

andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by negacy on 2009-11-26
> **atomizer said:**
> Is a bug, [see post 21 of this bugreport for solution]("https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217")
I followed the bug and updated my /etc/hosts file as shown below but that won't help. pls some help, still facing this problem.

127.0.0.1    localhost
127.0.1.1    negacy-laptop
 

216.34.181.59 downloads.sourceforge.net
212.219.56.167 kent.dl.sourceforge.net
213.203.218.122 mesh.dl.sourceforge.net
208.122.28.29 voxel.dl.sourceforge.net

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by jacobs444 on 2009-11-26
nevermind, im an idiot.

---

### Post by dddanmar on 2009-11-26
I personally find that to be a constant problem too...

---

### Post by dooglo on 2009-12-01
Having same issue here.  error with ttf-mscorefonts.installer

Karmic 9.10 32 bit

just a note, i'm new ubuntu.  so, i don't really understand how to fix.

i do like new things and am continually trying to figure out but can't this time.

D.

this is the error i get after uninstalling fonts and then rebooting and reinstalling


```
E: ttf-mscorefonts-installer: subprocess installed post-installation script returned error exit status 1
```


hope that helps.

---

### Post by shatul_in on 2010-02-19
[FONT=Lucida Console][SIZE=3][FONT=Times New Roman][B]Hello Friends,
I was completely disturbed with this problem since a month...
Now I got a workaround...
Just go to System-> Administration->Synaptic Package Manager and search for the concerned package which is "ttf-mscorefonts-installer" and make a right click and choose option "Mark for Complete Removal" and click on "Apply " above...
It will remove and no more issues in futue while installing any package....
Note: This package is only needed if you want to use Redmond's programs using Wine...else NOT....
Feel free to contact me.. [EMAIL="shatul_in@hotmail.com"]shatul_in@hotmail.com[/EMAIL][/FONT][/SIZE][/FONT]

---

