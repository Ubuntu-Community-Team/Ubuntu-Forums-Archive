---
title: "Unable to upgrade to 24.04 LTS &quot;Noble Numbat&quot; from 22.10 LTS"
date: 2024-08-16
forum: Installation &amp; Upgrades
---

### Post by freax-997 on 2024-08-16
Let me preface this by making it clear that I'm not very experienced with Ubuntu and Linux, in general. 

I am currently on Ubuntu 22.10 LTS.
So, a couple of weeks ago the Software Updater app started telling me this:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294099&stc=1[/IMG]

I click on Upgrade and authenticate it. The Software Updater then downloads two files for the release upgrade tool after which nothing happens. The Software Updater app closes on its own and does not install the OS upgrade. 

On trying the [FONT=courier new]sudo do-release-upgrade [FONT=arial]command[/FONT][/FONT], I get the following:
[FONT=courier new]
Continue [yN] y
Get:1 Upgrade tool signature [833 B]                                                                                                                                        
Get:2 Upgrade tool [1,282 kB]                                                                                                                                               
Fetched 1,283 kB in 0s (0 B/s)                                                                                                                                              
authenticate 'noble.tar.gz' against 'noble.tar.gz.gpg' 
extracting 'noble.tar.gz'

Reading cache

Checking package manager

Cannot upgrade 

An upgrade from 'kinetic' to 'noble' is not supported with this tool.

[FONT=arial]I have no idea what is happening here and how to resolve this issue. 
I would be very grateful if someone can help me out here. 

Thank you [/FONT]
[/FONT]

---

### Post by deadflowr on 2024-08-16
There is no clean upgrade path.
22.10 supported ended well before 24.04 came out.
(over a year)

Options are either backup and install a fresh copy of 24.04,
or backup and follow the basics of this guide: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Of the two options a fresh install will be quicker and less likely to fail as upgrading will need to move to 23.04 > 23.10 > 24.04.
Too many possible points of failure.

---

