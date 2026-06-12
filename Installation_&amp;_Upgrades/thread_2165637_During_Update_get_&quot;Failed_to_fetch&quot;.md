---
title: "During Update get &quot;Failed to fetch&quot;"
date: 2013-08-05
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2013-08-05
I am running Ubuntu 12.04.2 LTS.  When I tried to perform a routine update, I got:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.12_0.8.16~exp12ubuntu10.11_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.12_0.8.16~exp12ubuntu10.11_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.8.16~exp12ubuntu10.11_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.8.16~exp12ubuntu10.11_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-inst1.4_0.8.16~exp12ubuntu10.11_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/libapt-inst1.4_0.8.16~exp12ubuntu10.11_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.8.16~exp12ubuntu10.11_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.8.16~exp12ubuntu10.11_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.16~exp12ubuntu10.11_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.16~exp12ubuntu10.11_i386.deb) 404  Not Found [IP: 91.189.91.15 80]

I tried several times and always got the same message.  Can anybody tell me what to do????

---

### Post by Old_Grey_Wolf on 2013-08-05
Did you do sudo apt-get update before doing sudo apt-get upgrade? Those packages have been replaced by newer versions on that server.

---

### Post by Ralph L on 2013-08-05
Old Gray Wolf

Thank you very much for responding.  However, I do have a question.  I don't understand the apt-get upgrade command.  I don't want to upgrade to a newer version of Ubuntu (like Raring).  I want to continue using the 12.04 LTS version.  If I run apt-get upgrade will I be upgraded to a new version (as would be done in Update Manager), or will I just get the latest version of 12.04 LTS.  I am a little afraid to run the apt-get upgrade command.

---

### Post by QIII on 2013-08-05
Hello!

There is a lot of confusion around this:  upgrade and dist-upgrade do not change your version.

They upgrade the packages in the context of your current version.  

The update command does not do anything to actually change your applications/packages.  It only updates the list of what is available for upgrade.  To get new packages, you have to run upgrade or dist-upgrade.

The command that you ***don't ***want to do is do-release-upgrade -- which is what you could use to upgrade you to a new version of Ubuntu.

Best wishes!

---

### Post by Bashing-om on 2013-08-05
Ralph L; Hey ,
Allow me to intercede.

"apt-get upgrade" only updates installed packages as existing on the current install. 
To see the relevant info; do in terminal:
```

man apt-get

```
Do:
```

sudo apt-get update ##syncs the system data base with the repository
sudo apt-get upgrade ##updates installed packages

```
In the event you have "old" software sources repositories enabled ... got some work cut out for us to get all squared away.
On a production server, General advise is to be aware of what is being updated !

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Ralph L on 2013-08-05
Thanks everybody.  The apt-get update did the trick.  The I ran Update Manager from the main menu.  Everything worked.  And thanks for the explanation of apt-get upgrade.  I wasn't sure about it even after I read the man page.

---

