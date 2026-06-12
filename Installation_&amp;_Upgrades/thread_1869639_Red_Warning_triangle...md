---
title: "Red Warning triangle.."
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by bill23 on 2011-10-26
[COLOR=Red]**Red Warning triangle..**[/COLOR] 			 			 			 		 		  		  		
At  the top of my monitor on the right side is a red triangle warning icon.  I pass my cursor over it and a balloon appears telling me "The update  date is out of date. This may be caused by network problems or by a  repository that is no longer available. please update manually by  clicking on this icon and then selecting 'Check for updates' and check  if some of the listed repositories fail."

I have clicked on the icon opened Update manager to check on any updates. I get these error messages first; 

[U]Could not download all repository indexes

The repository may no longer be available or could not be contacted  because of network problems. If available an older version of the failed  index will be used. Otherwise the repository will be ignored. Check  your network connection and ensure the repository address in the  preferences is correct.[/U] 

I close it out and this one pops up; 

_An error occurred_

[U]The following details are provided:

E:Could not get lock /var/lib/apt/lists/lock-open (11:Resource temporarily unavailable)
E:Unable to lock the list directory.[/U]

I went to the Update Manager using System > Administration >  Update Manager it runs its little thing and indicates there are no  updates. Now I did do an update which may be a reason behind this? I  have Opera as one of my web browsers, there is a new version Opera  11.52. I downloaded the update and installed 'Opera_11.52.1100_i386.deb'

I may have seen something on the page announcing the update about using  the systems update system or manager? I seem to recall trying it but it  did not show any update in the Update Manager nor in the Systematic  Package Manager. When the update window showed up today, I did as stated  downloaded the update and installed the package.

I do not know if this may have in some way caused the system to detect  an error or what repositories are not reporting in or exactly what is  wrong? I am using Ubuntu 10.10 at the moment. 

Any and all help would be appreciated very much, TIA

bill23

---

### Post by dino99 on 2011-10-26
use synaptic instead of update-manager and check the tabs settings

sudo apt-get install synaptic
sudo synaptic

---

### Post by bill23 on 2011-10-26
I had already checked the Synaptic Package Manager an it did not show any new upgrades. I used your code:
sudo apt-get install synaptic, it showed I had the latest version.

bill23

---

### Post by plucky on 2011-10-26
> **bill23 said:**
> I had already checked the Synaptic Package Manager an it did not show any new upgrades. I used your code:
sudo apt-get install synaptic, it showed I had the latest version.

bill23

Post output from a terminal for ```
sudo apt-get update && sudo apt-get upgrade
```

Make sure all the other package managers are closed so you don't get the message ```
E:Could not get lock /var/lib/apt/lists/lock-open (11:Resource temporarily unavailable)
E:Unable to lock the list directory.

```

Good Luck

---

### Post by coffeecat on 2011-10-26
@bill23, please use non-default font and colour sparingly and only for highlighting purposes.

---

### Post by bill23 on 2011-10-26
Plucky,

How can you be certain beyond a shadow of a doubt that all your 'package managers' are closed? I have only used the 'Synaptic Package Manager' and 'Update Manager' If I have mistakenly used another 'package manager' I was not aware of doing so? Closing either of these two I usually go to the red 'X' at the top and click on it. Sometimes I will click the button at the lower left marked CLOSE. Is there one way which is sure to close the Package Manager completely so there is no chance it will be mistakenly thought to be still open?

Here is what happened after entering the command: sudo apt-get  update && sudo  apt-get upgrade.



```
bill48@bill48-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for bill48: 
Ign cdrom://Xubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427) natty Release.gpg
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en          
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en_US
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release.gpg                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release.gpg                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_US
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release                     
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main i386 Packages
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe i386 Packages
Get:5 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,202B]
Get:6 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [779B]
Media change: please insert the disc labeled                                   
 'Xubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)'
in the drive '/cdrom/' and press enter

Ign cdrom://Xubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)/ natty/main Translation-en
Ign cdrom://Xubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)/ natty/main Translation-en_US
Ign cdrom://Xubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)/ natty/restricted Translation-en
Ign cdrom://Xubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)/ natty/restricted Translation-en_US
Ign cdrom://Xubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427) natty/main i386 Packages/DiffIndex
Ign cdrom://Xubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427) natty/restricted i386 Packages/DiffIndex
Fetched 5,071B in 40s (126B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

You may have noticed the Xubuntu 11.04 Natty Narwhal in there. A while back i had major difficulty upgrading from Ubuntu 10.10 to 11.04. My PC did not have the right equipment to handle Ubuntu 11.04. Someone suggested using either Xubuntu 11.04 or Lubuntu 11.04 as alternatives. I burned both iso unto CD's and tried to install the Xubuntu 11.04. I must have done something wrong because it did not install in the regular sense of the word. It did install in the sense that if i have an update to complete it i need to reinsert the Disc in my CD drive so the 'system' recognizes it and the update can be complete. Weird, right?

Now this comment is directed at all out there.
What is the point of having different fonts and colors if someone is going to smack you down because you used your own creativity and used a non default font or a non default color every so often? If the powers that be only want one font and or color then do not give us options. I understand some of the colors and fonts may not show up on everyones computers. If so then remove the ones most likely to not show up, don't leave them there because some one is sure to use them.

Okay, I'll get off my soapbox.

bill23

---

### Post by plucky on 2011-10-27
> How can you be certain beyond a shadow of a doubt that all your 'package managers' are closed? 

You cannot.The lock message tells you that there are two package managers running.It is only a warning.Sometimes Update Manager will run in the background just after you start up your system.

> Media change: please insert the disc labeled
'Xubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427)'
in the drive '/cdrom/' and press enter


Open Software Sources and un-tick (or delete) the Xubuntu CDrom as a source and hopefully your Red Triangle will disappear.

Good Luck

---

### Post by lisati on 2011-10-27
@bill23, some of us are getting older and have trouble with reading "loud" posts. Yes, I know there's a subjective part to this, but this forum is made up of people from a wide range of backgrounds and levels of tolerance. Using "code" tags (or similar) probably wouldn't hurt either when you're quoting log entries and error messages.

---

### Post by coffeecat on 2011-10-27
> **bill23 said:**
> What is the point of having different fonts and colors if someone is going to smack you down because you used your own creativity and used a non default font or a non default color every so often?

Just to add to what lisati has said, there are also members with severe visual acuity problems who are regular contributors to this forum. They need to use assistive technologies to be able to read posts, but even with the use of these, non-standard fonts and colours can cause problems for them. Also, you agreed to the [forum Code of Conduct](http://ubuntuforums.org/index.php?page=policy) when you registered, which includes:

> ...you agree that forum staff have the right to remove, edit, move or close any post, topic or thread at any time they see fit following the guidelines outlined below.

And

> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Staff routinely edit posts that fail to adhere to these guidelines.

> **lisati said:**
> Using "code" tags (or similar) probably wouldn't hurt either when you're quoting log entries and error messages.

Indeed. And since the use of code tags is a similar issue, I shall edit the relevant post forthwith.

@bill23, you might find this BBCode link useful:

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

