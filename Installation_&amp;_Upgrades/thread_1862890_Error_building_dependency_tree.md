---
title: "Error building dependency tree"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by andremmf on 2011-10-17
Hello,

I've just upgraded from 11.04 to 11.10 and i got this problem.
I've created a script to upgrade my system 
```

sudo apt-get update -m
sudo apt-get dist-upgrade -y
sudo apt-get autoclean -y
sudo apt-get autoremove -y
sudo apt-get update -m 

```
And i used it right after the upgrade, rebooted and tried to reinstall gnome with "sudo apt-get install gnome", but it stops on "Building dependency tree...0%" and after a few seconds it returns to terminal command input.
Can someone help me?
Thanks in advance.

---

### Post by 23dornot23d on 2011-10-17
probably hits dependency problems ..... 

I would use it and install aptitude

> 
sudo aptitude update
sudo aptitude safe-upgrade -y
sudo aptitude autoclean -y
sudo aptitude update
less chance or a dependency issue as aptitude tends to try to find solutions ....
and will not install packages if a dependency problem exists.

The one above worked for me not sure why you would update again at the end though ..........

I now did mine like this ..... and it works ..... like it .... too 

> 
sudo aptitude update
sudo aptitude safe-upgrade -y
sudo aptitude autoclean -y
sudo apt-get update
sudo apt-get autoclean -y
sudo apt-get autoremove -y
I still prefer to see what I am about to upgrade before I do it though ...


The failure is because you are trying to install older gnome 2 packages ..... we are now in Gnome 3

> 
gnomeshell@userxx-MS-7181:~$ sudo apt-get install gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome : Depends: gnome-desktop-environment (= 1:2.30+7ubuntu3) but it is not going to be installed
E: Broken packages
gnomeshell@userxx-MS-7181:~$ 

what you probably want is the fallback mode

> 
gnomeshell@userxx-MS-7181:~$ sudo apt-get install gnome-session-fallback
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-session-fallback is already the newest version.
gnome-session-fallback set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
gnomeshell@userxx-MS-7181:~$ 

see this thread they were discussing it ...
[http://ubuntuforums.org/showthread.php?t=1861063](http://ubuntuforums.org/showthread.php?t=1861063)



I have just revised this a little more ..... and I like the way this works now
My way ...... not saying its the right way ..... but its the way that will clear out old things
and make way for the new .... and allow a safe-upgrade to take place ..... 


gedit fupgrade.sh

add the following to it 

> 
sudo apt-get update
sudo apt-get install aptitude
sudo apt-get autoclean -y
sudo apt-get autoremove -y 
sudo aptitude update
sudo aptitude safe-upgrade -y
sudo aptitude autoclean -y

and then save it .....

Heres one I did earlier to [[COLOR=Red]**download**[/COLOR]]("https://sites.google.com/site/23dsources/home/source-lists/fupgrade.sh?attredirects=0&d=1") for anyone wanting to try it .... you still need to
do the following commands. 

then to make it executable

chmod u+x fupgrade.sh

then to run it

./fupgrade.sh

---

