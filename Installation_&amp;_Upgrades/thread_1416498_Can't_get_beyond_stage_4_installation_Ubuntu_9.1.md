---
title: "Can't get beyond stage 4 installation Ubuntu 9.1"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by puzzledboy on 2010-02-26
Purchased second hand computer with no O.S installed and so decided to install Ubuntu 9.1. Got to page 4 and a brown progress bar appeared and ran from left to right until it got to 47% then stopped for about 20 secs. After that it disappeared and so I clicked forward to go to step 5 but I got a message saying 'No root file system defined'. 'Correct this from partition menu'.
How do I do this, could someone please help using simple non technical language click by click please?

---

### Post by darkod on 2010-02-26
That would usually happen if you select Advanced (Manual) partitioning in step 4 but you hit forward without specifying the mount points (root and swap as minimum).

Look here in the screenshots to figure out are you getting the same screens:
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Also, for a start, if you want only ubuntu on your hdd I would recommend just selecting Erase and use whole disk option in step 4. That will set up ubuntu automatically on the whole hdd.

---

### Post by puzzledboy on 2010-02-26
Thank you Darkrod for your help.
In step 3 I click foward to go to step 4. I then see a box headed 'Starting up partitioner' it also says 'scanning discs'. the progress bar gets up to 47% and remains there for about 1 minute. the screen then goes white and says 'step 4' in the bottom left corner. the top of the screen says 'Prepare partitions'. There are various headings like device etc, however the screen remains blank. I waited 45 mins but screen stayed blank. Hitting forward throws up a message box headed 'no root system'. In the box it says 'No root system is defined please correct this from the partitioning menu'. However this is impossible as I never got to see the partitioning menu. I've been over this several times and always get the same result. Can you or anyone suggest what I should do next

---

### Post by Sef on 2010-02-26
What partitioning option have you selected?

---

### Post by puzzledboy on 2010-02-26
Thank you Sef for your help but I have not seen any thing on the screen offering me any partitioning option,that is the problem.

---

### Post by darkod on 2010-02-26
> **puzzledboy said:**
> Thank you Sef for your help but I have not seen any thing on the screen offering me any partitioning option,that is the problem.

I think I know what your problem is. The step 4 partitioner is not showing any partitions/disk at all. This happens with 9.10 installer if you have used the disk in raid earlier and it has raid meta data on it.

If you are NOT running raid on your computer, load the live desktop first (Try Ubuntu option) and in terminal do:

sudo dmraid -E -r /dev/sda (if you have one hdd it would be /dev/sda, if not sure ask)
sudo apt-get remove dmraid

Note that if you are running raid the above commands might break your array, so DO NOT run them. If you are using raid you need to install ubuntu in different way, with the alternate install cd.

---

### Post by puzzledboy on 2010-02-26
Thank you Darkrod ,
I do not know what raid means.I bought the computer second hand with  no O.S. on it.
So I do not know if this thing called "raid" is on it or not.
You say load live desk top first.How do I do this? By this I mean where do I go to get this and what to click on?
What is "terminal" and where do I find it?
I do not know what breaking my array means.
The machine has only got one HDD.
What is the alternative  install C.D. and where can I get one?
I have been using Ubuntu 9.1 purchased from the Linux shop.
I know that I could have downloaded and burnt a disc for free over the internet but the instructions were too difficult for me to understand and so I bought one.
As you can see I know nothing about computers so I am grateful for any help that I can get but I do need it in very simple language and in step by step form.

---

### Post by darkod on 2010-02-26
OK. Boot the computer with the ubuntu cd inside and in the menu you see select Try Ubuntu without changes to your computer. That will load ubuntu running from the cd, so it's usually called live desktop.
Go in Applications-Accessories and there you have Terminal.
Execute both commands one by one (you need to hit enter after each):

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid

You need to type exactly because linux makes difference between small letters and capital. The first command should ask you whether you want to delete the raid data, just say yes.

After that you can close the terminal. There will be Install icon on the desktop, you can click on it to start the install.

When you reach step 4 the screen will look differently this time we hope, if you want to use only ubuntu on the computer it's best to select the Erase and use whole disk option. That will install ubuntu taking the whole hard disk.

Don't worry about the alternate install cd right now, I don't think you will need it.

---

### Post by puzzledboy on 2010-02-26
Thank you Darkrod,
I will carry out your suggestion tomorrow (Saturday) as it is getting a bit late now.
Probably in the afternoon as I must go shoping in the morning.
I will report back on what happens

---

### Post by puzzledboy on 2010-02-27
Hello Darkrod,
I did as you suggested and here is what I saw on the screen,
 
To run a command as administrator (user "root"),use "sudo <command>".
 
   [EMAIL="ubuntu@ubuntu:-$"]ubuntu@ubuntu:-$[/EMAIL] (after the $  there was a flashing small black block andI began typing at that point)
(after the colon sign which comes after the second word ubuntu is a symbol a bit like a letter "s" on its side but the keyboard on this laptop does not have this and so I have had to use a horizontal dash sign instead)
 
After typing in the first line which you gave to me and hitting enter I got the following message,
 
sudo: dmraid-E-r/dev/sda:command not found
 
Should there be spaces any where between the symbols? I did not use any spaces except  between sudo and dmraid?

---

### Post by puzzledboy on 2010-02-27
Hello Darkrod,
A strange yellow face like symbol has appeared on my message.I do not know how this happened or what it means.
After [EMAIL="ubuntu@ubuntu"]ubuntu@ubuntu[/EMAIL] I put  a colon.
Also I see that the words [EMAIL="ubuntu@ubuntu"]ubuntu@ubuntu[/EMAIL] keeps coming  up in blue and I can't understand this either as I typed in using black on white. Sorry about  these errors but I have to type with one finger and keep making lots of mistakes .

---

### Post by darkod on 2010-02-27
> **puzzledboy said:**
> Hello Darkrod,
I did as you suggested and here is what I saw on the screen,
 
To run a command as administrator (user "root"),use "sudo <command>".
 
   ubuntu@ubuntu:-$ (after the $  there was a flashing small black block andI began typing at that point)
(after the colon sign which comes after the second word ubuntu is a symbol a bit like a letter "s" on its side but the keyboard on this laptop does not have this and so I have had to use a horizontal dash sign instead)
 
After typing in the first line which you gave to me and hitting enter I got the following message,
 
sudo: dmraid-E-r/dev/sda:command not found
 
Should there be spaces any where between the symbols? I did not use any spaces except  between sudo and dmraid?

Yes, exactly as I typed it. There are spaces after dmraid, after -E, and after -r. That's why it didn't recognize the command, it thinks the whole line is the command.

---

### Post by puzzledboy on 2010-02-27
Hello Darkrod,
Went back to computer and entered,
 
sudo    dmraid    -E    -r    /dev/sda     (note I have exaggerated the spaces to clarify and emphasise what I typed in. In reality they were single spaces)
 
After hitting enter a message appeared saying,
 
"No block devices found"
 
Should I now go ahead with the second line?

---

### Post by darkod on 2010-02-27
Yes, but the raid issue doesn't seem to be your problem.

Can you also post the result of:

sudo fdisk -l (small L)

---

### Post by puzzledboy on 2010-02-27
Hello Darkrod
I typed in sudo fdisk-l
Reply, command not found.
 
I also typed in sudo fdisk -l
Reply  [EMAIL="ubuntu@ubuntu:-$"]ubuntu@ubuntu:-$[/EMAIL] followed by flashing black and white cursor.
 
 
I also entered the second line of your previous 2 suggestions
reply was  Reading package lists...done
                Building dependancy tree
                Reading state information...Done
                The folowing packages will be REMOVED: dmraid
0 upgraded, 0 newly installed 1 to remove and 0 not upgraded
After this operation, 176kB disk space will be freed. Do you want to continue
                             [Y/n]?

---

### Post by darkod on 2010-02-27
Are you sure your hard disk is working OK and visible at all? It seems after all this that it's either not connected well or not working. the fdisk command should return information about your hdd and the partitions on it and it returned nothing for you.

You have to make sure the hdd is enabled in BIOS and recognized. If you enter the BIOS and look inside does it show a hdd is even installed? Does the hdd have the data and power cables connected correctly?

---

### Post by puzzledboy on 2010-02-27
Hello Darkrod
I think HD is OK,I can hear a whirring noise from the region where it is located in the computer ,definately not the fan noise.
BIOS shows a HD is installed and returns its size.
I do not understand the BIOS menu or the various settings but I have found the following.
                   Standard CMOS features
 
IDE HDD Channel 0 Master [HL-DT-STDVD-ROM-GD R8]
 
IDE HDD Autodetection
1st Boot device  Floppy
2nd Boot device Hard disc
3rd Boot device CD ROM
 
I would have to open up the computer case to check connections.
 
Does any of the above give any clues?
 
My main PC , running Windows XP, developed the freezing mouse problem.
After getting a lot of help from a website called Geekstogo involving breaking and remaking all connections and  cleaning using compressed air it still would not work.At their suggestion I put in a new IDE cable but no result.The CPU is running very hot and now they suggest fitting a new PSU and if this dooes not work then fit a new fan unit and if this does not work then fit a new motherboard. All of this is what is what is known as test by replacement.However I would end up replacing lots of components that probably do not need replacing (at great expense) before solving the problem.
 So I decided to buy a second hand compter and install Ubuntu .
I have added this last paragraph to explain why I want to run Ubuntu

---

### Post by darkod on 2010-02-27
It seems it only reports the dvd-rom as master on channel 0. You should be able to hit Enter on HDD Autodetection and it will try to detect it.
Also in the boot devices it's better to have cdrom before hdd because when you insert ubuntu cd and want to boot from it, cdrom needs to be before hdd. If no bootable cd is in the drive it would boot from hdd anyway.

If you're not familiar with hardware, ask some friend for help to check the connections. It looks like it's not connected properly, or even worse, not working at all.

---

### Post by puzzledboy on 2010-02-27
Hello Darkrod
I changed the boot order so that the CDROM now comes before theHDD as you suggested. I hit enter on HDD Autodetction  but with no resut shown.The help page in the BIOS says that hitting enter in HDD Autodetection will throw up a list of essential data about the HDD but it does not.
Your conclusions are I think correct and so I have sent an e-mail to the vendors pointing out that the HDD cannot be accessed.
Thank you for  all your help .

---

### Post by puzzledboy on 2010-03-18
Hello Darkrod
 
I took computer back to the vendor who found that the machine had no hard drive
The previous owner had removed it and physically destroyed it because there was sensitive data present.
They fitted a 520 MB hard drive and loaded Windows XP Pro onto it.As soon as I got it home I validated the programme with Microsoft and it appears genuine.I then downloaded AVG anti virus and ran a complete disc check which found 5 trojan horse infections which it put into the virus vault. Now my question is can I use my Ubuntu disc to partition the hard drive and install Ubuntu one one portion and retain Windows XP on the other portion without harming Windows XP?
Will the viruses which are now confined in the virus vault interfere with the partitioning or with Ubuntu itself?

---

