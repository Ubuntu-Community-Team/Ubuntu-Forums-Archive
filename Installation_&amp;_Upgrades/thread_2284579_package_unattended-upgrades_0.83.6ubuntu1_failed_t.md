---
title: "package unattended-upgrades 0.83.6ubuntu1 failed to install/upgrade: subprocess insta"
date: 2015-06-30
forum: Installation &amp; Upgrades
---

### Post by dburdick-d on 2015-06-30
This is the actual bug report that I reported due to an error from ubuntu's automatic updates.  I received updates this morning and then an error while updating due to unattended-upgrades.  Ubuntu support said it's not a bug or an issue that they can help with.  However I reported the bug from the error window from the updates while all the updates failed because of this error.  Can someone please tell me why this happened, and why ubuntu is not helping out with this update.  This is their and mine comments:  [TABLE]
[TR]
[TD][Marc Deslauriers (mdeslaur)]("https://launchpad.net/%7Emdeslaur")             wrote             41 minutes ago:                          [/TD]
                       [TD="class: bug-comment-index"]           [ #2]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1470111/comments/2")           [/TD]
         [/TR]
            [/TABLE]
                               Relevant part of your upgrade log:
 insserv: warning: script 'K27dcservice' missing LSB tags and overrides
insserv: warning: script 'dcservice' missing LSB tags and overrides
insserv: There is a loop between service dcservice and grub-common if started
insserv:  loop involving service grub-common at depth 5
insserv:  loop involving service dcservice at depth 2
insserv: There is a loop between service dcservice and grub-common if started
 This is unrelated to the unattended-upgrades package.
 Do you have any idea what the dcservice init script is? It looks like it's causing a systemd deadlock.

              
                [TABLE="class: bug-activity"]
               [TR]
         [TD="colspan: 2"]Changed in unattended-upgrades (Ubuntu): [/TD]
       [/TR]
          [TR]
       [TD="align: right"]         **status**:       [/TD]
       [TD]         New &#8594; Incomplete       [/TD]
     [/TR]
    [/TABLE]
             
                                                                                            [TABLE]
                [TR]
           [TD]             [Deryk Burdick (dburdick-d)]("https://launchpad.net/%7Edburdick-d")             wrote             23 minutes ago:                          [/TD]
                       [TD="class: bug-comment-index"]           [ #3]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1470111/comments/3")           [/TD]
         [/TR]
            [/TABLE]
   
                            Marc,
 I actually have no clue what the dcservice init script is.  And why  the systemd deadlock occuring is beyond my control.  I am still new to  linux and learning its performance and coding as well as it's functions  to better control the open program.   I am turning to you to help with  this issue.

 When installing updates from ubuntu this error occured and didn't fully install the other updates.
 Please help figure this out Marc,  let me know what you can do to make this better.

              
        
                                                                                        [TABLE]
                [TR]
           [TD]             [Marc Deslauriers (mdeslaur)]("https://launchpad.net/%7Emdeslaur")             wrote             15 minutes ago:                          [/TD]
                       [TD="class: bug-comment-index"]           [ #4]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1470111/comments/4")           [/TD]
         [/TR]
            [/TABLE]
   
                            I'm sorry, but I can't help you with your issue.
 Perhaps you can try asking on [http://askubuntu.com](http://askubuntu.com) or in a support forum like [http://ubuntuforums.org/](http://ubuntuforums.org/) .
 Since this is a support issue, and not a problem with the unattended-upgrades package, I am closing this bug.

              
                               [TABLE="class: bug-activity"]
[TR]
         [TD="colspan: 2"]Changed in unattended-upgrades (Ubuntu): [/TD]
       [/TR]
          [TR]
       [TD="align: right"]         **status**:       [/TD]
       [TD]         Incomplete &#8594; Invalid       [/TD]
[/TR]
[/TABLE]
[h=1]What to do now as this is not taken care of???  Please help as this Ubuntu program and it's developers don't care to take care of this issue that came from their servers!!!???  Should I just uninstall Ubuntu as there is no support for it or what?  I am loosing trust in this program cause the developers just don't care...




    package unattended-upgrades 0.83.6ubuntu1 failed to install/upgrade:  subprocess installed post-installation script returned error exit  status 1[/h]                                                               Bug #1470111 reported by       [Deryk Burdick]("https://launchpad.net/%7Edburdick-d")       1 hour ago                    
             
                                                       
                                                               
                        [8]("https://bugs.launchpad.net/+help-bugs/bug-heat.html")       
                            This bug affects 1 person     
           [TABLE="class: listing"]
                [TR]
           [TH="colspan: 2"]Affects[/TH]
           [TH]Status[/TH]
           [TH]Importance[/TH]
           [TH]Assigned to[/TH]
           [TH]Milestone[/TH]
         [/TR]
                                      [TR="class: highlight"]
     [TD]       [         &#8203;       ]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1470111/+editstatus")     [/TD]
          [TD]                             [unattended-upgrades (Ubuntu)]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades")                                                [/TD]
                 [TD]                                    [Invalid]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1470111/+editstatus")           [             [IMG]https://bugs.launchpad.net/@@/edit[/IMG]           ]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1470111/+editstatus")                
     [/TD]
           [TD]                Undecided       
     [/TD]
      [TD]                                                                            Unassigned                                                                              [/TD]
      [TD]                                         
     
[/TD]
         [/TR]
                                    [/TABLE]
                 [Also affects project]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1470111/+choose-affected-product")         [(?)]("https://bugs.launchpad.net/+help-bugs/also-affects-project-help.html")               [Also affects distribution/package]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1470111/+distrotask")          [Nominate for series]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1470111/+nominate")          
                                                                [h=3]Bug Description[/h]   
    While new updates were installing, this one update would not install.  Issues preventing it to install.
 ProblemType: Package
DistroRelease: Ubuntu 15.04
Package: unattended-upgrades 0.83.6ubuntu1
ProcVersionSignature: Ubuntu 3.19.0-21.21-generic 3.19.8
Uname: Linux 3.19.0-21-generic x86_64
ApportVersion: 2.17.2-0ubuntu1.1
Architecture: amd64
Date: Tue Jun 30 09:22:08 2015
DuplicateSignature: package:unattended-upgrades:0.83.6ubuntu1:subprocess installed post-installation script returned error exit status 1
ErrorMessage: subprocess installed post-installation script returned error exit status 1
InstallationDate: Installed on 2015-06-22 (7 days ago)
InstallationMedia: Ubuntu 15.04 "Vivid Vervet" - Release amd64 (20150422)
PackageArchitecture: all
RelatedPackageVersions:
 dpkg 1.17.25ubuntu1
 apt  1.0.9.7ubuntu4
SourcePackage: unattended-upgrades
Title: package unattended-upgrades 0.83.6ubuntu1 failed to  install/upgrade: subprocess installed post-installation script returned  error exit status 1
UpgradeStatus: No upgrade log present (probably fresh install)

---

### Post by matt_symes on 2015-06-30
Hi

Opdn a terminal and type these commands. Post back the entire output into your next post.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
dpkg -S K27dcservice
```

The capital letters above are important.

Kind regards

---

### Post by tgalati4 on 2015-07-01
Welcome to the forums.  If you are new to Linux, then I would install 14.04 which a Long Term Support (LTS) version, with less bugs and more support.  Unless you have a really good reason to run 15.04, there are a lot of new frameworks (including systemd) which will take some time to mature and stabilize.

---

