---
title: "Log-in problem after upgrading to Ubuntu 10.04 Lucid: solution"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by robertlzw on 2010-05-31
Today I upgraded from Ubuntu 9.10 Karmic to Ubuntu 10.04 SLT (Lucid) and found I could no longer logged in the newly installed, lovely Ubuntu 10.04 SLT (Lucid). After pulling my hair for hours in addition to waiting patiently for upgrading operations to complet, I at last figured the solution and feel happy now. I hope you would never pulling your hair as I did and enjoy it.
 
(1) system environment
My previously installed Ubuntu 9.10 Karmic is on an Windows XP using VMware player running live CD images from Windows XP's hard disk following instructions of this link:
[http://www.tanguay.info/web2008/tutorial.php?idCode=installUbuntuOnVmware](http://www.tanguay.info/web2008/tutorial.php?idCode=installUbuntuOnVmware)
 
(2) Upgrading
I used "Synaptic Package Manager" for the upgrading. Basically, my system detected that Ubuntu 10.04 was available and I just went ahead with upgrading it.
 
(3) Nightmare
After about 2 hours upgrading, I at last saw the log-in window of Ubuntu 10.04 and eagerly tried my hands on its. To my great disappearment, there is no response from my keyborad, no key can be entered, although my mouse works well. My keyboard no longer worked. I tried changing boost order, even changed the root password from there, it helped little. This was a very difficult situation, as I could do nothing before I could sucessfully log into it (my previous projects could have been gone forever!).
 
(4) Solution
When my native keyborad did not work, I used the "on-screen keyborad" to log in and succeded. The details are in fact given in the following link of sombody else:
[http://www.clickonf5.org/linux/keyboard-problem-ubuntu-1004-login-vmware/7163](http://www.clickonf5.org/linux/keyboard-problem-ubuntu-1004-login-vmware/7163)
 
However, up to this point, I still could not use my native keyboard to log in(I am using the keyborad of Dell Inspiron 6400 laptop, by the way) and have to rely on the "on-screen keyborad" for logging in. It is very inconvenient for me. So after loging in sucessfully with the "on-screen keyborad", I did the following setups for my specific keyboard (you might as well):
(a) go to "System->Preferences->keyboard->layouts", click on the default "unknown" button after the "keyborad mode" prompt.
 
(b) in the "Vendors:" frame window, select "Dell", in the "Models:" frame window, selet "Dell Laptop/notebook Inspiron 6xxx/8xxxx", click ok. 
 
(c) Then click the "Apply System-Wide" button bellow it for it to take effect. Shut down and restart. 
 
Now I can use my native keyborad rather than the "on-screen keyborad" to log into the Ubuntu 10.04 (both now works). Do the same for your native keyboard.
 
(P.S.: At one point, I almost wanted to wipe out Ubuntux completely when pulling my hairs for hours. However, now I feel very happy that it works and I have the updated system. I hope you do as well.)

---

