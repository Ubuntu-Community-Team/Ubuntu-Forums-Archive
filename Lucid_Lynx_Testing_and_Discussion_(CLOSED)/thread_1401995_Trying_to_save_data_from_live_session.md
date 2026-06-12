---
title: "Trying to save data from live session?"
date: 2010-02-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-02-08
I'm almost ashamed and thought about posting this in Absolute Beginners :redface:

I created a fairly large file today running the Lucid Live daily CD (testing Gparted after the update) and I wanted to save it to my Jaunty /home.

Well duh, I've never done that before. I usually use an external USB drive with Ubuntu installed to transfer or rescue data and that's a snap!

I've even used a Live CD to recover data like "sudo /bin/bash" & "mkdir /media/disk" & "yada-yada" but that seems like overkill. I just wanted to be able to copy one new folder from a Live session to my installed Juanty /home.

For the moment I just used a DVD RW and got it done but I'd really like to know how to do this simply without a Kabuki dance ;)

What am I overlooking to gain the ability to "write" to a partition on my hard drive?

---

### Post by cherva on 2010-02-08
First you have to know that your partitions are in /dev/sdaX where X is the number of the partition.
Then you can mount these partitions in any directory you want with ```
sudo mount /dev/sdaX /any/whare/you/want
``` and then you can read/write to this partition only as root ... I think if you mount in in a directory that other users have write access to they can write too but I'm not completely sure about that :)

---

### Post by mdurham on 2010-02-08
Is it possible to use Nautilus and double-click on the partition where home resides? This would mount it automatically wouldn't it?
Cheers, Mike

PS
What happened to the kansasnoob picture?

---

### Post by cherva on 2010-02-08
I think that last time I booted a 9.10 live cd it mouned my partitions as soon as I clicked on them in nautilus yes :) ,but I'm a terminal guy :)

---

### Post by kansasnoob on 2010-02-08
> What happened to the kansasnoob picture?

What picture?

If you're trying to be cute it's not working!

---

### Post by kansasnoob on 2010-02-08
> **cherva said:**
> I think that last time I booted a 9.10 live cd it mouned my partitions as soon as I clicked on them in nautilus yes :) ,but I'm a terminal guy :)

To 'read" yes! I'm trying to figure out how to "write' from a live session to an existing partition.

---

### Post by VMC on 2010-02-08
Not quite sure what or how you created a folder on a livecd, but what I did was use the "Places> <partition of choice>", then mount to see how it got mounted then having nothing but live folders I copied /var to <partition of choice>/home, like so:

sudo cp -r /var /media/123xyz/home

It copied all 88 megs. To my  <partition of choice>/home folder as /var

Edit:I'm not clear even to myself... So I picked from "Places" one of my partitions that was recognized, and used that to copy to.

---

### Post by seeker5528 on 2010-02-08
> **VMC said:**
> sudo cp -r /var /media/123xyz/home


I thought you were root when running from the Live CD, meaning no sudo required. 

Assuming the user account these are being copied into are the primary Ubuntu user (created during installation) you probably want to do.

chown -R 1000:1000 /path/to/files/*

:the '-R' tells chown to work recursively, you can leave it out if you are doing a single file or if all the files are in the same directory.

If it is not your primary Ubuntu user account then you will need to do:

ls -ld /path/to/partition/home/*

: to see what the numerical uid:gid are.

Later, Seeker

---

### Post by mc4man on 2010-02-08
Or just do graphically - mount the partition, then  
Alt+F2 - gksu nautilus - filesystem - media -blah, blah.

(there's a chance if  you use a 6+ char password that if you set up a user on the livecd the same as your normal with same password you could write without sudo - can't try here because my pass is 1

---

### Post by ronacc on 2010-02-08
if it is your home partition in jaunty you can just copy it with nautilus , I do it all the time , click Or double click on the partition to mount it then just copy and paste or drag and drop as suits you . If the "home" in jaunty has a different user name use gkudo to start nautilus , you will just have to change the ownership of the file when you get back to jaunty .

---

### Post by seeker5528 on 2010-02-08
> **mc4man said:**
> (there's a chance if  you use a 6+ char password that if you set up a user on the livecd the same as your normal with same password you could write without sudo - can't try here because my pass is 1

That might work, if it is not your primary account you will still have to know the numerical UID and GID so you can specify them when you create the user account.

And if the files were created before doing that, you will still have to chown them.

If you browse in Nautilus to the location of your directory you want to copy to, then right click the directory, click on 'Properties' then click on the permissions tab, it will show you the UID next to 'Owner:' and the GID next to 'Group:'

Nautilus doesn't give you the option to type these in so you will still have to chown the files, or if you would prefer to deal wit it later.

If you wait until you are booted into your installation on the hard drive, then do:

gksu nautilus --no-desktop

You can select the files/directories in question, right click, select properties, go to the permissions tab and change the owner and group there.

Later, Seeker

---

### Post by VMC on 2010-02-08
> **mc4man said:**
> Or just do graphically - mount the partition, then  
Alt+F2 - gksu nautilus - filesystem - media -blah, blah.

(there's a chance if  you use a 6+ char password that if you set up a user on the livecd the same as your normal with same password you could write without sudo - can't try here because my pass is 1

gksu nautilus didn't work on my Livecd. It thought about it then died. But I still needed to *sudo* the mount and move commands.

---

### Post by mdurham on 2010-02-09
> **kansasnoob said:**
> What picture?

If you're trying to be cute it's not working!

Sorry about that kansasnoob, I mixed you up with someone else.
Cheers

---

### Post by kansasnoob on 2010-02-09
> **mdurham said:**
> Sorry about that kansasnoob, I mixed you up with someone else.
Cheers

I'm sorry to be a grouchy old fart, I'm irritated with a few things right now and my sense of humor stinks :frown:

I shouldn't take it out on Ubuntu community members.

---

### Post by kansasnoob on 2010-02-09
Somehow I'm still not getting this concept. Color me dumb :confused:

Consider I can mount any partition while in a live session and read anything. I can mount any USB drive and copy to it quite simply.

But I can't for the life of me figure out how to easily copy a file to or gain "write" privileges to a partition on the main drive.

Example: sda6 is my Jaunty /home and I create a file of any sort and want to save it to Jaunty's /home.

Can't do it. Or even if I want to edit the text in Jaunty's /home/documents - can't do it.

I could go to Gparted and delete the whole partition but trying to save something to it requires a Kabuki dance :p

For obvious reasons one doesn't want to change permissions, etc. Another odd thing - with ntfsprogs I can abuse the crap out of my Win and save anything I want there ;)

This did give me an excuse to try out Ubuntu One which is fine, and I can save to any external media I wish.

I hope I'm thought provoking :)

---

### Post by ronacc on 2010-02-09
I hadn't tried it from the live cd , I regularly copy from partition to partition on regular installs . This method works with the live cd , I just tested it . Open a browser window as user and mount the partition you want as "target" , it will then show up when you open a root nautilus ( sudo nautilus) , open a root nautilus and you can copy to or edit files on the "target" . You have to mount the partition as user to get it to show up as a partition in the root nautilus .Only a little more effort than from an install .

---

### Post by mc4man on 2010-02-09
> if you set up a user on the livecd the same as your normal with same password you could write without sudo

Actually turns out to be very simple (if you don't have a flash card ect. handy)

Just create a user with the same name as your install (partition)  you want to copy to - the password doesn't need to be the same (or if a non- install partition the same name as owner 

Then log out and back in as that user, mount the partition and do whatever you wish - no sudo needed, anything copied over will be owned by you when you boot back to real install

> will still have to know the numerical UID and GID so you can specify them when you create the user account

Irrelevant - not needed

---

### Post by ranch hand on 2010-02-09
I think it is easier to NOT save it to another partition.  Save it to the Live Session desktop.  Open Nautilus and copy the bugger anywhere you want it to be.

---

### Post by kansasnoob on 2010-02-10
Gosh, I've played around off and on for a couple of days and can't seem to figure this out :confused:

As I said I can easily save data created using the Live Desktop to any of my USB storage drives, or to my NTFS partition on the internal drive, but I can not for the life of me save anything created in the Live Desktop to one of my Ubuntu /home partitions.

I've even tried creating a new user with the same name and passwd as I use in my installed OS's then restarting X, and it's still a no-go. I'm reluctant to change permissions on those partitions.

Now, it's not a big deal. It's just something I'd never tried before but it puzzles me????? Oddly I tried the Hardy (8.04.4) Live CD and had no problem so maybe it has to do with changes in hal :confused:

Then again maybe I'm just not understanding something, it wouldn't be the first time I was clueless :)

---

### Post by VMC on 2010-02-10
> **kansasnoob said:**
> Gosh, I've played around off and on for a couple of days and can't seem to figure this out :confused:

As I said I can easily save data created using the Live Desktop to any of my USB storage drives, or to my NTFS partition on the internal drive, but I can not for the life of me save anything created in the Live Desktop to one of my Ubuntu /home partitions.

I've even tried creating a new user with the same name and passwd as I use in my installed OS's then restarting X, and it's still a no-go. I'm reluctant to change permissions on those partitions.

Now, it's not a big deal. It's just something I'd never tried before but it puzzles me????? Oddly I tried the Hardy (8.04.4) Live CD and had no problem so maybe it has to do with changes in hal :confused:

Then again maybe I'm just not understanding something, it wouldn't be the first time I was clueless :)
Strange. Now I have a better picture of your issue. That LiveCD you reference is in fact a CD and not a LiveUSB, correct? If so, try to do what I did just for sake of argument. Copy LiveCD "/var" to "/home/var" and see if you can. If so then it has to do with the LiveCD created files.

---

### Post by nystire on 2010-02-12
Another (not so nice) option would be to copy the files over in a root shell and then when you reboot into the other OS, run chown on them to change the owner to you current user. 

Or - if you are the only person who uses the computer, or trust the other people who use it - simply use 'chmod 777 <file>', replacing <file> with the actual file name. That way, everybody who uses the computer can access them.

---

### Post by seeker5528 on 2010-02-12
For me it didn't seem to be a big problem to copy stuff.

For my test I opened Gedit, created a couple of test documents.

Went to places and clicked the drive I wanted to save to.

Closed the resulting Nautilus window.

Opened a terminal window and typed:

gsku nautilus

: browsed to /home/ubuntu to find the saved documents.

Right clicked and selected copy.

Browsed to /media/blah/blah to get to my home directory on the HDD.

Right clicked and selected paste.

This is using a Karmic DVD, but as far as I can tell it is the same live session the CD uses.

The process should be the same with a Lucid CD/DVD.

All that's left at that point is to change the ownership of the files, which as indicated previously, if you wait until you are booted into your HDD installation you can do in Nautilus by opening a terminal window and typing:

gksu 'nautilus --no-desktop'

: browse to the location you copied the files to and select properties and and go to the permissions tab then select the owner and group.

I could have sworn this worked the other day when I selected multiple items, but today it won't let me change the ownership of a selected group only if I have selected an individual file or directory. If I select a single directory and change the ownership it does give me the option to apply the changes to enclosed files, so if you plan an using Nautilus to change ownership later and you have more than a couple of files, you probably want to create a new directory to copy the files into so you can use the option to apply the changes to the enclosed files to do them all at once.

EDIT: 
Scratch that, the option to apply changes to enclosed files doesn't seem to do anything, so if there are more than a couple of files it looks like the best option is still to open a terminal window and do:

sudo chown -R *username:groupname* /some/directory/*

Later, Seeker

---

### Post by mc4man on 2010-02-12
@kansasnoob
At the risk of beating a dead horse, don't know why either of the 2 ways doesn't work for you.

In the absence of an external drive/flash card to save to I'd do the same name deal over gksu nautilus or sudo whatever - are you logging out from the default of "ubuntu" and logging back in as the named user?

On a lucid live cd now - as mentioned quite simple - created a new user same name as I use - "doug", using a different password because it won't allow 1 - (123456

Then logged out, logged in as doug, mounted my hardy install using the live cd admin. password of nothing (enter on keyboard) and have full read/write on the hardy partition. (or my karmic one if I wished

See screen - transferring a folder, next screen shows permissions of the transferred file inside.

(same idea as dual/tri, ect.- booting, if the user name of the admin. user is the same then you have full permissions without auth. ect..

---

### Post by seeker5528 on 2010-02-12
> **mc4man said:**
> @kansasnoob(same idea as dual/tri, ect.- booting, if the user name of the admin. user is the same then you have full permissions without auth. ect..

That's not something you can assume to be true.

In Debian and Ubuntu based distributions there is an expectation that the first UID and GID will start at 1000, some distribution may start at 500.

Also if the user in question is not the admin user and you create a user account with the same name, first user will have a numerical UID and GID of 1000 if you don't specify what to use for these which may require you to create the group first so you can specify the numerical GID. The numerical UID and GID have to match, the names don't. 

So if the installed system had 2 accounts 'fu' and 'bar' the user in question was the second user with numerical UID:GID of 1001:1001 and while running the live session you create a single user 'bar' and don't specify that it should use 1001 for the numerical UID and 1001 for the numerical GID....  Now you have a user in the live CD session named 'bar' with a numerical IDs of 1000 for the user and group, so if you browse to what would be /home in the installed system and look at the properties for the user home directories, for the 'fu' direcory it would show owner and group of 'bar' and for the 'bar' directory it would show owner and group of 1001 assuming you did not create more than one user in the live session.

Later, Seeker

---

