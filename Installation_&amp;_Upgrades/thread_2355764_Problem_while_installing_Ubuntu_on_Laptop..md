---
title: "Problem while installing Ubuntu on Laptop."
date: 2017-03-16
forum: Installation &amp; Upgrades
---

### Post by manad2 on 2017-03-16
Hello , 

I'm trying to install the latest Ubuntu version from an DVD , created with Windows 10 burn image to disk .
When starting installation after a while i get this prompt :[http://prntscr.com/ekof9l](http://prntscr.com/ekof9l) , and than it stucks to this : [http://prntscr.com/ekofku](http://prntscr.com/ekofku) , no matter what options i choose from the first prompt .

Waited for over 3hours ,with no answer or error message.

---

### Post by coffeecat on 2017-03-16
Support thread. 

*Thread moved to **Installation & Upgrades**.*

A question so that you can provide some information that those helping may need. Have you read through, and do you understand, the message in the "Force UEFI Installation?" popup window showing in your first screenshot? It would be unwise to force installation in that situation for the reason given. Please provide more details of your system, including what operating system is already there. If you don't understand the message or the difference between UEFI and legacy BIOS, there are many here who can help you.

---

### Post by manad2 on 2017-03-16
I use an laptop Assus x540S Type C , latest Bios version 303. 
I did read a bit about the difference between Uefi and Legacy but it's still unclear for me .

After choosing not to force the instalation and waiting an while i got this error : [http://prntscr.com/ekosnv](http://prntscr.com/ekosnv) , i didnt create the partition myself i choose to be created automaticaly.

Edit: I dont have any OS on it and dont intend to use anything else except ubuntu on that laptop.

---

### Post by RobGoss on 2017-03-16
Hello and welcome, If you intend to install only Ubuntu on this laptop then the installation should be straight forward this guide should give you the help needed to begin your installation [https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop) 

Is there another OS on this machine or is it a blank hard drive?

Here's more information about UEFI and things you should be aware of before you begin your installation [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by manad2 on 2017-03-17
Hey , i think there's leftovers from another OS on that HDD or several other OS .
Tried to reformat using GPARTED , got this error : [http://prntscr.com/el3cfd](http://prntscr.com/el3cfd) ,[http://prntscr.com/el3cl4](http://prntscr.com/el3cl4) ! 

For some reason nothing can partition this Hdd , not Ubuntu or Linux or Windows.. nothing ... .

---

### Post by manad2 on 2017-03-18
Any1 can help ? It would be greatly apreciated .

---

### Post by mörgæs on 2017-03-19
Let's begin with the beginning. Are you able to run a live boot?

---

### Post by manad2 on 2017-03-19
Yes i've been able to boot from DVD and USB , i've managed to delete and create new partitions chossing Something else but i cant get past this error :
I tried formating the HDD and creating /swap , /root , /home , /boot manualy and still getting this error .

---

### Post by Autodave on 2017-03-19
Is there  a reason why you are choosing "Something else"? If not, try going with "erase disk and install".

---

### Post by manad2 on 2017-03-19
I did tried with erase disk and install first same error  , than after searching on google for the error someome recomanded to go with something else and create that partition format..

---

### Post by RobGoss on 2017-03-19
Did you also create a mount point  **/** along with the swap partition?

---

### Post by manad2 on 2017-03-19
I created this exact partitions: [COLOR=#000000] /swap , /, /home , /boot[/COLOR]

---

### Post by mörgæs on 2017-03-20
And did you add a boot flag?

---

### Post by manad2 on 2017-03-20
I dont think so , how do i add that ?

---

### Post by mörgæs on 2017-03-21
First of all, it *should* not be necessary in GNU/Linux but as a desperate attempt...
You can set it using Gparted.

---

### Post by RobGoss on 2017-03-21
Open up Gparted and navigate were you see Partitions, scroll down a ways and you will see manage flags

---

### Post by manad2 on 2017-03-22
[COLOR=#000000]Tried to reformat using GPARTED , got this error : [/COLOR][http://prntscr.com/el3cfd](http://prntscr.com/el3cfd)[COLOR=#000000] ,[/COLOR][http://prntscr.com/el3cl4](http://prntscr.com/el3cl4)[COLOR=#000000] ! [/COLOR]

---

### Post by oldfred on 2017-03-22
Lets see all your current partitions:
sudo parted -l
sudo fdisk -lu

If drive was ever used on a RAID configuration, that leaves meta-data that must be erased. 
Or if you used Windows to convert a gpt drive to MBR, that leaves a backup gpt partition table and Linux tools see both MBR & gpt and get confused.
Rarely with new drive, it could even be a hard drive issue.

---

### Post by manad2 on 2017-03-24
Aparently that it was, took the laptop back into warranty , the service said the HDD failed and that was the issue , thank you all for your support .

---

### Post by RobGoss on 2017-03-24
Glad you were able to pin point were the the problem was

---

