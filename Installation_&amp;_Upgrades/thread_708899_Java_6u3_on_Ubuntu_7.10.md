---
title: "Java 6u3 on Ubuntu 7.10"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by RickyOswaldIOW on 2008-02-26
Hi there, I'm a linux newb and I'm having a bit of trouble installing Java 6 Update 3.  I'm following the instructions on the site ([http://java.com/en/download/help/5000010500.xml#rpm](http://java.com/en/download/help/5000010500.xml#rpm)).  I've got as far as step 6 but when I try step 7 the terminal tells me that rpm is not installed and so I type "apt-get install rpm" which does some stuff but eventually gives me the following:
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libbeecrypt6 libneon25 librpm4
Suggested packages:
  alien
The following NEW packages will be installed
  libbeecrypt6 libneon25 librpm4 rpm
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory


And thus I am unable to proceed.  I could of course try out the standard non-rpm one but since I have come this far with the rpm package and I have no idea how to reverse the changes that I have already made, I am reluctant to do so.  Can anybody help me?

---

### Post by taurus on 2008-02-26
First, you shouldn't get the .rpm.  Should grab the .bin and install it from a terminal.

However, you can install sun java from a terminal with

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

And before you run those two commands to install java from a terminal, make sure you have close down Add/Remove or synaptic first since you cannot run two apps that use adept at the same time.  And that is why you get that error message.

---

### Post by RickyOswaldIOW on 2008-02-26
Aha I see!  So my problem was that I was trying to install the rpm from the terminal whilst I had the Package Manager open?  Well, I went back and installed the regualr .bin and it worked fine but I'll make a note of your instructions for next time :)

Considering how far I got with the rpm files, is it safe to simply delete them (the rpm.bin and .rpm files)?

---

### Post by taurus on 2008-02-26
Yes, it's safe to delete the **filename**.rpm and even the **filename**.bin after you have installed it.  Don't need them anymore.

---

### Post by RickyOswaldIOW on 2008-02-26
I have completed the steps in the installation guide on the java website without issue but upon testing at [http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp) it does not seem to be functioning.
   I have tried clearing the cache and I also closed all of the firefox windows and made sure that "Enable Java" was checked in the preferences.
   I then proceeded to try the method that you suggested using sudo commands and after the second command has executed I am shown a blue manual inside the terminal with a button that says "Ok" but I cannot click it so I simply closed the console window...

---

### Post by taurus on 2008-02-26
When you install java, you will be greeted with a license window so you need to except it before it will install on your machine.  You need to highlight the <OK> with the Tab key and then Return key.

---

### Post by RickyOswaldIOW on 2008-02-26
Okay, I see.  I have tried to enter the sudo commands again but on the first one I get the message:
> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


Should I switch to su and type in "dpkg --configure -a"?

---

### Post by taurus on 2008-02-26
Just run

```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by RickyOswaldIOW on 2008-02-27
Excellent, this works perfectly :)
Thankyou very much for your help.  I do have one other request, can you point me towards some information that explains installing and running applications and updates in linux?  I have come straight from the MS Windows environment and I am finding the concept a little difficult to grasp right now.

---

### Post by taurus on 2008-02-27
Here ya go, [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/).

---

