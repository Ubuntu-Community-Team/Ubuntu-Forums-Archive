---
title: "Unable to install wine E:Malformed line 53 in source list /etc/apt/sources.list (dist"
date: 2020-06-26
forum: Installation &amp; Upgrades
---

### Post by lintoleomathew on 2020-06-26
I am getting the entry 53 error. please help me to solve this. i am using Lubuntu 18.04 Bionic


while running 
sudo apt-get -f install

E: Malformed entry 53 in list file /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
E: Malformed entry 53 in list file /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.




while running 
```
cat -n /etc/apt/sources.list


     1    # deb cdrom:[Lubuntu 16.04.1 LTS _Xenial Xerus_ - Release i386 (20160720)]/ xenial main multiverse restricted universe
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic main restricted
     6    # deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
    11    # deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team, and may not be under a free licence. Please satisfy yourself as to
    15    ## your rights to use the software. Also, please note that software in
    16    ## universe WILL NOT receive any review or updates from the Ubuntu security
    17    ## team.
    18    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic universe
    19    # deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial universe
    20    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates universe
    21    # deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-updates universe
    22    
    23    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    24    ## team, and may not be under a free licence. Please satisfy yourself as to 
    25    ## your rights to use the software. Also, please note that software in 
    26    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    27    ## security team.
    28    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic multiverse
    29    # deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial multiverse
    30    deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
    31    # deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
    32    
    33    ## N.B. software from this repository may not have been tested as
    34    ## extensively as that contained in the main release, although it includes
    35    ## newer versions of some applications which may provide useful features.
    36    ## Also, please note that software in backports WILL NOT receive any review
    37    ## or updates from the Ubuntu security team.
    38    # deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
    39    
    40    ## Uncomment the following two lines to add software from Canonical's
    41    ## 'partner' repository.
    42    ## This software is not part of Ubuntu, but is offered by Canonical and the
    43    ## respective vendors as a service to Ubuntu users.
    44    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    45    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    46    
    47    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
    48    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
    49    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
    50    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    51    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
    52    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
    53    deb sudo add-apt-repository sudo add-apt-repository deb
    54    # deb-src sudo add-apt-repository sudo add-apt-repository deb
```

---

### Post by CatKiller on 2020-06-26
You can see that you've randomly added commands to the file rather than the entries that should be there.

---

### Post by ActionParsnip on 2020-06-27
Delete line 53. It's a shell command (ish) and not a valid entry in sources.list

---

### Post by lintoleomathew on 2020-06-27
Sir, i am a newbie in ubuntu..Could you please detail your reply. Thanks for the reply

---

### Post by overdrank on 2020-06-27
Hi and welcome, this link may help
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by howefield on 2020-06-27
In your terminal use...

```
sudo nano /etc/apt/sources.list
```

Scroll down to the two lines (as per your output above) and remove them. Then Ctrl + o ,  press enter and then Ctrl + x to finish.

You could make a copy of the file before doing this so you can get back to your starting point lest you make the situation worse.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```

---

### Post by Holger_Gehrke on 2020-06-27
The last two lines of the sources.list file look like you tried to follow some tutorial on how to install some program from an unusual source and got the instructions mixed up.

Open the file in an editor and delete those lines. Since /etc/apt/sources.list is a system configuration file, only the system administrator (called 'root' on unix-like systems) can write to that file. To become root for one command you use 'sudo' (**s**witch **u**ser and **do**) on the command line followed by the command to execute as root. For editing a file as root there's a specialized (and safer) tool called 'sudoedit'.

Enter 'sudoedit /etc/apt/sources.list' in a terminal. You will be asked for your password. Enter it. You will not see any feedback during typing, that's normal, it's a security measure to prevent people watching you enter the password finding out the length of your pw. An editor will open, probably 'nano' if you haven't configured sudoedit to use another editor. Go to the end of the file and remove the last two lines. Save the file (ctrl-o in nano) and exit the editor (ctrl-x in nano). Done.

Holger

---

### Post by ActionParsnip on 2020-06-30
Could use:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-2020-06-30
sudo sed -i '53d' /etc/apt/sources.list > /tmp/sources.list
cat /tmp/sources.list | sudo tee /etc/apt/sources.list > /dev/null
sudo apt-get update

```

You can roll back with
```

cat /etc/apt/sources.list-2020-06-30 | sudo tee /etc/apt/sources.list > /dev/null
sudo apt-get update

```

---

