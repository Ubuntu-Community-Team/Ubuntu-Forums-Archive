---
title: "Errors in compilations after the update, disabled 3rd party sources...?"
date: 2016-08-21
forum: Installation &amp; Upgrades
---

### Post by singularite on 2016-08-21
Hi !

I've just updated Ubuntu from 14 to 16, apparently without big trouble, but now I realize that I can't compile anymore my C++ audio project.
I've noticed the following warning :
[ATTACH=CONFIG]270785[/ATTACH]
So I tried to check all cases in this place of the Ubuntu Software Centre, I guess the audio related one is involved with my problem :
[ATTACH=CONFIG]270786[/ATTACH]
But I got this error message :
[ATTACH=CONFIG]270787[/ATTACH]

with the following details :
```
W:The repository 'cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., W:The repository 'http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu xenial Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., W:The repository 'http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu trusty Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., W:http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/dists/trusty/InRelease: Signature by key 165D673674A995B3E64BF0CF4F191A5A8844C542 uses weak digest algorithm (SHA1), E:Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs, E:Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found, E:Failed to fetch http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/source/Sources  404  Not Found, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Here is maybe some more informations :

```
alexandre@Alexandre-MBP:~$ ls -al /etc/apt/sources.list.d/
total 32
drwxr-xr-x 2 root root 4096 août  21 16:25 .
drwxr-xr-x 6 root root 4096 août  18 21:28 ..
-rw-r--r-- 1 root root  174 août  21 16:48 ubuntu-audio-dev-ppa-trusty.list
-rw-r--r-- 1 root root  144 août  18 17:32 ubuntu-audio-dev-ppa-trusty.list.distUpgrade
-rw-r--r-- 1 root root  174 août  21 16:48 ubuntu-audio-dev-ppa-trusty.list.save
-rw-r--r-- 1 root root  164 août  21 16:48 xorg-edgers-ppa-trusty.list
-rw-r--r-- 1 root root  134 août  18 17:32 xorg-edgers-ppa-trusty.list.distUpgrade
-rw-r--r-- 1 root root  164 août  21 16:48 xorg-edgers-ppa-trusty.list.save

```

Do you have any clue to solve this issue ?
Thank you !

---

### Post by oldos2er on 2016-08-21
If you updated to 16.04 (Xenial), you no longer want trusty sources, but xenial ones instead. And you should disable the cdrom source as well.

---

### Post by deadflowr on 2016-08-21
Note that you needed to revert the xorg-edgers ppa before the upgrade.
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa]("https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa")
> Be sure to revert this PPA before doing a release upgrade or the upgrade will not succeed. 
To revert to official packages, install the ppa-purge package and run "sudo ppa-purge xorg-edgers".
Not as if that has anything to do with the problem at hand, but maybe it does?...

Also note that there is no ppa for ubuntu-audio-dev for either 14.04 or 16.04.
The ppa only goes up to 13.04.
[https://launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/ppa]("https://launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/ppa")

So you'll want to simply remove that ppa altogether, it's probably where the connection error is from.

---

### Post by singularite on 2016-08-21
Ok, so I've removed them from the list, as it was right after the upgrade.
I tried sudo ppa-purge xorg-edgers but I get "Could not find package list for PPA: xorg-edgers ppa".

So...it might not be the cause of the problem. Is it possible that some libraries used to compile the C++ code have disappeared with the upgrade of something like this ?

---

### Post by singularite on 2016-08-22
Here is some more information about this issue.
The libraries used for the project are :
Sndio for the sound : [http://www.sndio.org/install.html](http://www.sndio.org/install.html)
ROOT  : [https://root.cern.ch/](https://root.cern.ch/)
Armadillo for maths : [http://arma.sourceforge.net/download.html](http://arma.sourceforge.net/download.html)

Here is the first compilation error : ```
......../signal.cc|141|error: no match for &#8216;operator==&#8217; (operand types are &#8216;std::ofstream {aka std::basic_ofstream<char>}&#8217; and &#8216;int&#8217;)|
```
Here is the piece of code : ```
void Signal::Ecriture_fichier_wav(vec & sig, double Dt,string nom_fichier)
{
    cout<<endl<<"=====Crée un fichier wav à partir du tableau ====fichier:"<<nom_fichier<<endl;




    //...... ouvre le fichier en ecriture..........................

    ofstream pfich(nom_fichier.c_str());
    if (pfich==0)                                                  // PROBLEM HERE
    {

        cerr<<" erreur ecriture fichier:"<<nom_fichier<<endl;
        return;
    }

...

```

So something has changed about ofstream pfich(nom_fichier.c_str()); 

This is a fonction which uses Sndio, the other errors are about something obscure in Armadillo codes, but it may just be related to the first error (a "required from here" links to the first error's).

I've tried to download and install the last versions of Sndio and Armadillo, I have tested Sndio alone (cf. Sndio installation guide) and it works (but I'm not sure that the working version is the last one).

---

### Post by steeldriver on 2016-08-22
Can you post a larger extract of the 'make' output (so we can see the actual compiler commands / errors / warnings)?

I suspect it's more likely to be a change in how the compiler handles pointer-to-integer comparisons, rather than a change in the std::ofstream API itself

See for example [std::ofstream == NULL won't compile for -std=gnu++11, any workaround?]("http://stackoverflow.com/questions/32589155/stdofstream-null-wont-compile-for-std-gnu11-any-workaround")

---

### Post by singularite on 2016-08-22
Thank you, this solved this error : ```
if (!pfich) 
```
Now I get errors about the library ROOT, I'm trying to update it.

---

### Post by singularite on 2016-08-22
I struggle to install the version 6 of ROOT on Ubuntu 16.04. The previous one 5.34/30  seems to be installed, but I get some "failure loading dependent  library" when I try some command, and errors when I compile the code :

[ATTACH=CONFIG]270808[/ATTACH]

---

### Post by singularite on 2016-08-27
The end of the story : **[https://root.cern.ch/phpBB3/viewtopic.php?f=3&t=22232](https://root.cern.ch/phpBB3/viewtopic.php?f=3&t=22232)**

---

