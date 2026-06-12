---
title: "post-reinstall data recovery?"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2010-06-21
a little knowledge once again proves to be a dangerous thing.

I am dreaming I expect but this weekend, after a failed upgrade to 10.04, I decided to revert to 9.04 (9.40?)

not thinking, at the Partitioner step, I just clicked on the "OK, overwrite 10.04" and then I saw the thing launch itself off on some "formatting". Generally that is a big OOOPS. but this was my back up laptop which generally only has copies of stuff off my desktop and so I didn't give it much thought.

Furthermore, I naively assumed that if the reinstall was going to wipe out everything on the HDD, it would give me a warning, right?

wrong. 9.04 reinstalled, everything seems to have been flattened.
at which point I started to wonder if there weren't just a few files unique to the laptop ....

again, not the end of the world but 
a) is there anyway of trying to recover some of the wiped files? are there ghost copies out there somewhere?

b) how SHOULD I have partitioned this so that in the future, should I have to reinstall Ubuntu, it won't zap everything (a dual partition I presume, with like 10% to Ubuntu and the balance for data?)

thanks

Peter

---

### Post by bruno9779 on 2010-06-21
You should have kept /home on a different partition.

Your best bet at recovering something would be testdisk.

It is a very powerful tool, for partition recovery. The chances of success are pretty high.

But keep in mind that it will make the system unbootable, so you will have to log in a LiveCD of LiveUSB and copy the files from the recovered partitions.

After this you will have to reinstall, very likely.

---

### Post by pjstock on 2010-06-22
thanks for the suggestion.
there seem to be many enthusiasts for TestDisk.
I read up as best I could on testdisk, installed and ran it. But either it isn't finding anything helpful or I don't know how to use it.

Basically, it seems to have found my big partition (plus a small swap partition) and then I mark them both as P (to list files?) and then I presume I have it WRITE.

it then says I have to reboot. which I did but I don't know what I am supposed to do at that point.

some screen shots are attached.

OK, assuming that testdisk is not finding anything interesting, I guess I should just move on with this clean reinstall of 9.04 with a small partition for Ubuntu and a larger one for data and /home.

question. is there a way to repartition the current single one into two without reinstalling 9.04?
not that it is a huge deal. I haven't used the machine yet.
but when I do try reinstalling and then choosing to use the slider thingee to size two distinct partitions, the Partitioner is proposing the new 9.04 on one partition and the old (yesterday's) 9.04 on the other partition. I just want one version of 9.04.

can I get rid of the old 9.04 somehow and just have a clean data partition?

Peter

---

### Post by bruno9779 on 2010-06-22
that 9.04 you see is your recovered data.

As I said before it is unbootable. Load a live session, mount the partition and copy your files.

when you reinstall, select "choose partitions manually" (probably you choose to install side by side)

---

### Post by pjstock on 2010-06-22
you think? I'll have a look

naive ignorant question - how do I "Mount" that partition?

Peter

---

### Post by darkod on 2010-06-22
In live mode just look in Places, it should be there.

As for earlier questions. One big flaw in your thinking is that you want to use the guided (automated) methods, but have more control of your partitions. Forget about that. Forget what the slider tells you (it always creates new installation ignoring existant ones).

For a real control of your system, use Manual Partitioning. ALWAYS!!!

That will allow you to create as many partitions as you want, with the size you want for each, and the mount point (which will make a difference how the partition will be used).

This is a quick idea how it would look, only a suggestion, you make your own plan:

I am assuming you are using only ubuntu, you have no windows in there. And you start with blank disk (you can delete all partition in the same Manual Partitioning step).

Create one primary partition, ext4, mount point /, size 10-15-20GB depending how much space you have to spare.

Then, create as logical partitions:
ext4, mount point /home, size as you wish
swap, swap area, size 2GB or if you hibernate regularly 1.5 * RAM size
(optional) ext4, mount point /data, size as you wish

I'm not sure what is exact purpose of /data except what the title says, but I've seen people use it. You can read online about difference of having single huge /home, or split that space between /home and /data.

The point of all the above is, the system is on your / partition, and you can do a clean install with formatting it at any time. That still keeps your data in /home and /data. But in the new clean install you have to specify those two partitions to be used again with mount points /home and /data, only DO NOT tick the format box.
Linux will not assume how to use them. You have to TELL it.

Forget about using the automated methods any more. Get control of your computer. IMHO.

---

### Post by pjstock on 2010-06-22
"In live mode just look in Places, it should be there."

Hmmm, under Places I see (can't seem to get a screenshot):

HomeFolder
Desktop
Documents 
Music
Pictures 
Video
Computer
38.3Gb Drive
Network
Connect to Server
Search for files
Recent Documents

and none of these locations seem to have anything in them, at least nothing resembling the MP3s and jpgs I am missing.

but again, assuming my data is lost, following your instructions for flexible partitioning.

just before I get to the Partitioner, I get the attached message?

I am not sure what it means or what I should do at this point.

---

### Post by bruno9779 on 2010-06-22
Mounted, means that it is active and available in the file system. If a storage device is connected but not mounted, you cannot access it's contents.

Partitions cannot be changed or edited while mounted, so this prompt asks you if you want to unmount them manually, or if the system should do that for you

---

### Post by pjstock on 2010-06-22
thank you Bruno

But going back to your earlier suggestion:

"As I said before it is unbootable. Load a live session, mount the partition and copy your files."

at what point do I "mount the partition"? what's the process? and how do I know the partition that might have my old data?

---

### Post by darkod on 2010-06-22
Do you know how big was your partition? The 38GB filesystem shown in Places might be it. If you click on it, you will mount it, so that's the point it gets mounted. After you click on it and it gets mounted, you can look inside what is there and what not.

Provided you did boot the ubuntu cd in live mode as said, it doesn't know what is what on your hdd, so in Places it will just display like 30GB filesystem, 100GB filesystem, etc.

---

### Post by pjstock on 2010-06-22
I presume the entire partition was 38.4gb because that was the entire HDD and I think/know that I installed 9.04 originally (and then again over the weekend) on just a single partition.


Just did a little search on that 38.4gb Place and there seems to be nothing familiar (I am looking for some audio files that I use in my radio work. 95% were copies from my desktop, but there might have been some unique files to this laptop.)

so, nothing I recognize. unless you have some other suggestion on where my recovered files would be (if there were any) I will just get on with a fresh new 2 partition reinstall.

---

### Post by bruno9779 on 2010-06-22
what can you see in the 38 GB partition?

If you installed on one single partition, in there you should see:

/bin
/boot
/cdrom
/dev
/etc
/home
/lib

....... and so on.

You files should be in /home.

---

### Post by darkod on 2010-06-22
> **pjstock said:**
> I presume the entire partition was 38.4gb because that was the entire HDD and I think/know that I installed 9.04 originally (and then again over the weekend) on just a single partition.


Just did a little search on that 38.4gb Place and there seems to be nothing familiar (I am looking for some audio files that I use in my radio work. 95% were copies from my desktop, but there might have been some unique files to this laptop.)

so, nothing I recognize. unless you have some other suggestion on where my recovered files would be (if there were any) I will just get on with a fresh new 2 partition reinstall.

Maybe hold on for second opinion, but if the files were not restored, I guess you could reinstall.

And did you mean 3 partition reinstall? If also creating swap, that would be swap, / and /home.

For a disk of only 40GB it would be like:

primary, / ext4 10GB
logical, swap 2GB
logical, /home ext4 the rest

---

### Post by pjstock on 2010-06-22
under /home there is

/peter (which I specified I think as the user when I reinstalled 9.04 to clear out the botched 10.xx upgrade that wouldn't boot this weekend.)

but in the folders under /peter (/documents /music etc.)
there is nothing.

here though is the log from my Testdisk shot. does it mean anything to you? it makes no sense to me.

---

### Post by darkod on 2010-06-22
I'm not too experienced with testdisk, but that
D Linux
D Linux Swap

means the deleted partitions were detected.

I'm not sure if you changed them, you can try running testdisk again. Using up/down to select the partition and left/right arrows to change the partition symbol, you need to probably change them into

* Linux
L Linux Swap

Because usually the root would be primary (not sure if bootable, grub doesn't use the boot flag), and the swap would be logical.

Set them as that, and write the partition table. You can't make it worse. :)

Then boot again with the cd in live mode, and check in Places, and the folder should be /home/username/....etc

---

### Post by darkod on 2010-06-22
PS. You don't mark them as P to list files, P is for primary when using the left/right arrows to set partition type.
With a partition highlighted you can hit the P key to list files. That way you can also see if the Linux partition has the files you need. Before writing the partition table changes.

---

### Post by pjstock on 2010-06-22
got it  (Or am getting it.)

when I ran Test Disk again and did a deeper search I get the attached result.
 
when I click down to the 2nd one, I get a red Structure Bad message. (which can't be good)

and when I hit ENter to see any files I get an "INvalid partition STructure" message (and no files.)


any clues anyone? before I give up.

---

### Post by darkod on 2010-06-22
> **pjstock said:**
> got it  (Or am getting it.)

when I ran Test Disk again and did a deeper search I get the attached result.
 
when I click down to the 2nd one, I get a red Structure Bad message. (which can't be good)

and when I hit ENter to see any files I get an "INvalid partition STructure" message (and no files.)


any clues anyone? before I give up.

The second partition shown is some NTFS partition which probably existed before your original ubuntu install. Why are you bothering with it when you are not trying to recover any data from it?

The main partition is the first one in the list (you don't care about the third one too because it was only swap partition). If you highlight the first one, and hit P to list files, what do you get?

Even if it doesn't list them, it's still worth to try this:

Highlight the first partition, hit left or right arrow until the symbol in front becomes *.
The highlight the third partition, again hit left/right until it becomes L.

Write the changes to the partition table.

Reboot with the cd in live mode and try to open the 38GB partition in Places.

PS. I just saw your username in the screenshot. Are you doing this from the ubuntu install? Use the live mode, do you know what it is? Boot with the ubuntu cd and select Try Ubuntu. That runs ubuntu from the cd, don't play with your hdd from your installed ubuntu. In fact, don't boot it because it lowers the chance to save the files from the previous install.

Note that testdisk might not be available in live mode until you go into System-Administration-Software Sources and enable the second repository in the list, the (universe). Then add testdisk and run it with:

sudo apt-get install testdisk
sudo testdisk

---

### Post by pjstock on 2010-06-22
thanks
I could not get TestDisk to install while booted from the CD. So I run it when booted from my harddisk, get the results and then flip to the LiveCD boot to do any fiddling.


is it fouling things up to run TestDisk when booted from the 9.04 install on my HDD?

thank you for your extreme patience.

I managed to install TestDisk in a LiveCD boot.
but when I run it, it doesn't seem to "see" the HDD. I think it is only analyzing the CD.

how do I run Testdisk in this "off the CD" boot mode so that it does the HDD as well?

Peter

yea, the way I am running testdisk it is only showing the CD.

how do I "point" it to include the HDD?

for others wondering the same thing.

to run Testdisk as Root you have to use the Sudo command.

so, instead of testdisk at the terminal prompt, type in

sudo testdisk


what this does, I have no clue. but it shows my HDD now.

---

### Post by darkod on 2010-06-22
I don't know whether you saw my PS I added to post #20:

> Note that testdisk might not be available in live mode until you go into  System-Administration-Software Sources and enable the second repository  in the list, the (universe). Then add testdisk and run it with:

sudo apt-get install testdisk
sudo testdisk

Anyway, how far did you get after managing to install and run testdisk from live mode?

Another important note, live mode doesn't keep the changes you make. So fater you reboot for example, you have to do the same procedure to "install" testdisk again.

The reason why it's better not to use the installed OS when trying to recover data, is that you prevent any writing to the hdd which is crucial to recover the data. If anything gets written on the hdd, nothing can recover the data that was written to that same block after that any more.

---

### Post by pjstock on 2010-06-22
thanks
I managed to finally analyse and write a partition table for the HDD, but on reboot, looking into the 38GB Place, there is nothing. no files whatsoever.

So, I'll mull it for a bit and then reinstall with 3 partitions as you suggested.

---

