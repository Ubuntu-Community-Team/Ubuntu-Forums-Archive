---
title: "Keyboard mapping on Ubuntu Server 12.04"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by Kendee on 2012-07-01
OK team, there are plenty of threads on this topic, most of which claim to be solved. But none of them tell me how to do it! At least following them doesn't get me there. I must be missing some vital piece of inherent knowledge, or something.

I created a VM of Ubuntu Server 12.04, and run it on my VMware Player (running on Ubuntu11.10 desktop). I don't get any options during the installation as VMware says that it will use 'Easy Install'. 

As expected, I only get the command line interface to my server. No problem, says I.

The timezone is set to PDT, so I hunt around the internet and find
sudo dpkg-reconfigure tzdata
Select Europe and then London, and all is well

I want to see what packages are installed so I run
dpkg -l | less

Only instead of  that my keyboard is mapped such that I get 
dpkg -l > less

Aha, says I, I need to change my keyboard map.
Again I hunt around the internet world and find
sudo dpkg-reconfigure console-data

console-data is not installed so I
sudo apt-get install console-data
and try again.
Whoop-de-doodle, all is well.

I can dpkg -l | less to my hearts content.

Until, that is, I reboot the server.

Where has my keyboard mapping gone?

As I said at the beginning there are numerous threads, most of which (despite the poster saying he in using Ubuntu Server) refer to actions to be taken through the GUI and are therefore not helpful. The rest refer to 
sudo dpkg-reconfigure console-setup
but give no instructions.

How do I know what encoding to use?
I selected UTF-8 and was presented with a confusing list of Character sets to choose from most of which look like they are commented out.
I make a guess at
#Latin1 and Latin5 - western Europe and Turkic languages
I am then asked what font to use
I tried Fixed
Now I am asked for font size
I take a stab at 16
Finally the selections end but the console now reports
/usr/bin/ckbcomp: Can not find file "symbols/uk" in any known directory
update-initramfs: deferring update (trigger activated)

What went wrong (and how do I fix it)?

BTW I tired various combinations in the selection process and none did what I want.

Any help would be gratefully received.

Thanks
Ken

---

