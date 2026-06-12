---
title: "Keyring problem"
date: 2024-08-01
forum: Installation &amp; Upgrades
---

### Post by Pierre Dartigues on 2024-08-01
Hi,
I am using Ubuntu 23.10. I'd like to upgrade to 24.04LTS. I get this message whenever I try:
> [COLOR=#000000]MyLaptop:~$ sudo apt install krename[/COLOR][COLOR=#000000][sudo] password for pieter:[/COLOR]
[COLOR=#000000]E: Conflicting values set for option Signed-By regarding source [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable: /usr/share/keyrings/opera-browser.gpg != /usr/share/keyrings/opera.gpg[/COLOR]
[COLOR=#000000]E: The list of sources could not be read.[/COLOR]

What can I do to correct this problem?

Thanks for replies!
Pierre

---

### Post by currentshaft on 2024-08-01
What's in /etc/apt/sources.list.d/ that relates to opera? Post those file contents here, please.

---

### Post by Pierre Dartigues on 2024-08-02
[COLOR=#000000]It seems not to be possible to do that. I copied those files to a temporary directory, then tried to upload them for attachments. I get the message "invalid file" when trying.

Is there any means to make it possible nevertheless? I will try to get the contents of the files.[/COLOR]

---

### Post by Pierre Dartigues on 2024-08-02
I think I managed nevertheless, see below:

opera.list :
> [COLOR=#000000]deb [signed-by=/usr/share/keyrings/opera.gpg] [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free[/COLOR]

opera.list.distUpgrade :
> deb [signed-by=/usr/share/keyrings/opera.gpg] [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free

opera.list.save :
> deb [signed-by=/usr/share/keyrings/opera.gpg] [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free

opera-archive.list
> deb [signed-by=/usr/share/keyrings/opera-browser.gpg] [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free

opera-stable.list :
> # This file makes sure that Opera Browser is kept up-to-date# as part of regular system upgrades


# deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases) disabled on upgrade to jammy disabled on upgrade to mantic

opera-stable.list.distUpgrade : 
> # This file makes sure that Opera Browser is kept up-to-date# as part of regular system upgrades


# deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases) disabled on upgrade to jammy disabled on upgrade to mantic

opera-stable.list.save :
> # This file makes sure that Opera Browser is kept up-to-date# as part of regular system upgrades


# deb [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases) disabled on upgrade to jammy disabled on upgrade to mantic

---

### Post by currentshaft on 2024-08-02
would remove all of those files and try again.

Opera is a terrible browser which no one should be using anyway.

---

### Post by Pierre Dartigues on 2024-08-02
I thought so. I tried to uninstall Opera but that is not easy neither maybe because of those files. But root is owner of those files and I cannot delete them just like that. I looked up the command > chown and changed ownership to myself but that did not open the possibility to delete those files.
What can I do?
I went into the directory > [COLOR=#000000]/etc/apt/sources.list.d/[/COLOR], > # sudo su
 #chown pieter opera* and then tried to delete those files using the file manager. Not possible. What can I do?

---

### Post by currentshaft on 2024-08-02
sudo find /etc/apt/sources.list.d/ -type f -name "opera*" -exec rm -fv {} \;

---

### Post by #&amp;thj^% on 2024-08-02
> **Pierre Dartigues said:**
> I thought so. I tried to uninstall Opera but that is not easy neither maybe because of those files.

You mean this won't work??
```
sudo apt remove opera-stable
```
Please show that return.

I also agree with currentshaft>>>"Opera is a terrible browser" :)

---

### Post by Pierre Dartigues on 2024-08-02
No, this iswhat happens:

> Asus:/etc/apt/sources.list.d# sudo apt remove opera-stableE: Conflicting values set for option Signed-By regarding source [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable: /usr/share/keyrings/opera-browser.gpg != /usr/share/keyrings/opera.gpg
E: The list of sources could not be read.




---

### Post by Pierre Dartigues on 2024-08-02
I am logged in as root while doing that...

---

### Post by #&amp;thj^% on 2024-08-02
Looks like that repository in your sources list uses the Signed-By option multiple times, so apt doesn't know which key to use to check the signature. Or maybe it's a related problem, but there seems to be a case of conflicting keys.

When we encounter the error, it&#8217;s usually because apt has found multiple conflicting instructions regarding the GPG key to verify a particular repository.

Specifically, this conflict arises from duplicated repository entries, incorrect or outdated GPG keys, or improperly configured repository settings. 

I think currentshaft is on track, I'll go away now...Good Luck

---

### Post by #&amp;thj^% on 2024-08-02
> **Pierre Dartigues said:**
> I am logged in as root while doing that...

That would have been good to know before hand, is it any different as your normal user?

EDIT: Can you show us this:
```
ls /etc/apt/keyrings/
```

---

### Post by #&amp;thj^% on 2024-08-02
Ok I'll start from the beginning for Opera
```
sudo apt install dirmngr ca-certificates software-properties-common apt-transport-https curl -y

```
Now import its GPG key
```
curl -fsSL https://deb.opera.com/archive.key | gpg --dearmor | sudo tee /usr/share/keyrings/opera.gpg > /dev/null
```
I'll add the Opera Browser&#8217;s APT repository 
```

Add the source
[code]echo deb [arch=amd64 signed-by=/usr/share/keyrings/opera.gpg] https://deb.opera.com/opera-stable/ stable non-free | sudo tee /etc/apt/sources.list.d/opera.list
```
install time:
```
sudo apt update 
sudo apt install opera-stable
```
I used it for couple minutes then I purged it:
```
sudo apt autoremove --purge opera-stable
REMOVING:                       
  chromium-codecs-ffmpeg-extra*  opera-stable*

Summary:
  Upgrading: 0, Installing: 0, Removing: 2, Not Upgrading: 0
  Freed space: 320 MB

Continue? [Y/n] 
(Reading database ... 399641 files and directories currently installed.)
Removing chromium-codecs-ffmpeg-extra (2:1snap1-0ubuntu2) ...
Removing opera-stable (112.0.5197.39) ...
Processing triggers for hicolor-icon-theme (0.18-1) ...
Processing triggers for gnome-menus (3.36.0-1.1ubuntu3) ...
Processing triggers for shared-mime-info (2.4-5) ...
Processing triggers for menu (2.1.50) ...
Processing triggers for desktop-file-utils (0.27-2build1) ...
(Reading database ... 399469 files and directories currently installed.)
Purging configuration files for opera-stable (112.0.5197.39) ...
Processing triggers for menu (2.1.50) ...

```

I'll look here:
```
ls /usr/share/keyrings/opera.gpg
/usr/share/keyrings/opera.gpg

```
I want that gone too:
```
 sudo rm -r /usr/share/keyrings/opera.gpg

```
Now:
```
ls /usr/share/keyrings/opera.gpg
ls: cannot access '/usr/share/keyrings/opera.gpg': No such file or directory

```
Now back to normal:
```
 ls /usr/share/keyrings/
brave-browser-archive-keyring.gpg          ubuntu-pro-anbox-cloud.gpg
brave-browser-beta-archive-keyring.gpg     ubuntu-pro-cc-eal.gpg
brave-browser-nightly-archive-keyring.gpg  ubuntu-pro-cis.gpg
protonvpn-stable-archive-keyring.gpg       ubuntu-pro-esm-apps.gpg
ubuntu-archive-keyring.gpg                 ubuntu-pro-esm-infra.gpg
ubuntu-archive-removed-keys.gpg            ubuntu-pro-fips.gpg
ubuntu-cloudimage-keyring.gpg              ubuntu-pro-fips-preview.gpg
ubuntu-cloudimage-removed-keys.gpg         ubuntu-pro-realtime-kernel.gpg
ubuntu-master-keyring.gpg                  ubuntu-pro-ros.gpg

```

---

### Post by Pierre Dartigues on 2024-08-04
There is no response:> Asus:~$ ls /etc/apt/keyrings/
Asus:~$ 




---

### Post by Pierre Dartigues on 2024-08-04
These are the responses I get from the proposed entries:
> 
root@Asus:~# sudo apt install dirmngr ca-certificates software-properties-common apt-transport-https curl -y
E: Conflicting values set for option Signed-By regarding source [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable: /usr/share/keyrings/opera-browser.gpg != /usr/share/keyrings/opera.gpg
E: The list of sources could not be read.

root@Asus:~# curl -fsSL [https://deb.opera.com/archive.key](https://deb.opera.com/archive.key) | gpg --dearmor | sudo tee /usr/share/keyrings/opera.gpg > /dev/null
root@Asus:~# 

root@Asus:~# echo deb [arch=amd64 signed-by=/usr/share/keyrings/opera.gpg] [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free | sudo tee /etc/apt/sources.list.d/opera.list
deb [arch=amd64 signed-by=/usr/share/keyrings/opera.gpg] [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable non-free
root@Asus:~# 



root@Asus:~# sudo apt update
E: Conflicting values set for option Signed-By regarding source [https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/) stable: /usr/share/keyrings/opera-browser.gpg != /usr/share/keyrings/opera.gpg
E: The list of sources could not be read.
root@Asus:~# 


But: Somehow my trial removing the opera-files from > [COLOR=#000000]*/etc/apt/sources.list.d*[/COLOR] succeeded. I ignore why now it worked an earliar it did not...
I will try out what happens now after I performed a reboot.

---

### Post by Pierre Dartigues on 2024-08-04
:PAfter that I have been able to remove successfully the opera* files from > */etc/apt/sources.list.d* all of the commands you proposed in #13 succeeded and I was able to install new software again.
I am very grateful for your help, I have been coping with this problem for at least three months and now it's solved.
Thanks a lot!
:KS

---

### Post by #&amp;thj^% on 2024-08-04
Great News. Happy to hear that.
As a help to others please mark as Solved.

---

