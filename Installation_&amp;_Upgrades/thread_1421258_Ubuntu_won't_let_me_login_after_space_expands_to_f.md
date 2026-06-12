---
title: "Ubuntu won't let me login after space expands to full"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by JamezQ on 2010-03-04
I was using ubuntu fine then I get the message that I only have 19 gb's left . Strage as I had 89 gbs used on a 350 gb partition. So somehow it expanded that fast without me downloading anything. When I loged back in it says I don't have gnome-power installed, or a similar message and I can put in my password but it just takes me back to the login screen. I'm using ubuntu 10.04 AMD64. I did run a check and a huge amount of my data was in .private. 

How can i get my ubuntu back? Also is this a bug or just my error, it would be great if it was a bug, so the ubuntu developers can fix it, I'm using an alpha so I did sign up for this.

I can login to terminal by pressing cntrl alt f1-f6. And putting in my pass, so i can run commands and edit config files on nano if needed.


Edit: Even worse news, I cant get my data from this live cd. It says I have set up encryption wrong, and i dont know how to transfer important data to my flash drive using terminal.

---

### Post by yogesh.girikumar on 2010-03-04
Hi,

You can try to find out which folder is occupying so much space. Press CTRL+ALT+F2 to go to a terminal. Got to / directory by doing:
```
$ cd /
```

Try the following command when you are in / :
```
$ sudo du -hx --max-depth=1 | less
```
This will give you a list of directories with the space occupied by each directory in the first column. Do it with sudo because there may be some directories that are owned by the root.

Find out which is occupying an unusually lot of space. Let's say a directory named '.tempdir' is occupying a lot of space, go into the directory and execute the command again. Do this recursively and see if you find any directory with unusually large size. This might help determine what is causing the problem.

> It says I have set up encryption wrong, and i dont know how to transfer important data to my flash drive using terminal.

You can try to recover your data. 
See: [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
Also: [http://ubuntuforums.org/showthread.php?t=1357556](http://ubuntuforums.org/showthread.php?t=1357556)
[http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)

Since you're using Lucid alpha. There could be bugs. It is not recommended to use an alpha operating system for main stream usage unless you do it purely for experimenting , learning or development. You can instead use a stable version such as Karmic.

HTH

---

### Post by JamezQ on 2010-03-04
I tried a to un encrypt it from the live cd, I can't get it to work no matter what I do. I can view the file from inside though. So can you tell me how to copy that file to my flash drive, or even a unencrypted part of my disk maybe? So I can access on the live cd

Edit: Awesome, I'm able to use mv to move any file to an unencrypted part of that file system so I can get it later. 

Also TY for the disclaimer but i'm aware :) I like seeing how things are chaging so quickly, I never really "rode" a release before so i wanted to try it out. Anyway I will keep posting when I can run those commands you gave me for finding out the size.

---

### Post by yogesh.girikumar on 2010-03-04
Hi,

First thing you need to do is find out if your pen drive is detected.

Go into the terminal by pressing CTRL+ALT+F1
Go into super user mode by executing the following command:
  ```
 $ sudo bash
```
  
Give the password if prompted. Type the following command
   ```
# fdisk -l
```
   
You will get a list of your partitions and it's info. It must look something like this
```
/dev/sda1 * 1 3647 29239445 83 Linux
/dev/sda1 3648 5969 18654263 5 Extended
/dev/sda1 5970 19457 936542 83 Linux
```

Now plug in your flashdrive # Now execute fdisk -l again # There'll be an extra row in the list. Must start with something like:
  ```
 /dev/sdb1  
```
   
The '/dev/sdb1' is your flash drive. Now you have to mount it. Execute the following command.
```
   # mkdir /mnt/flashdrive
   # mount /dev/sdb1 /mnt/flashdrive
```
   
This will mount the flash drive to /mnt/flashdrive # Now you need to copy your files to /mnt/flashdrive using the cp command # Navigate to the directory where your files are and copy them to the /mnt/flashdrive directory
Here is an example of copying two files from my home directory to the flashdrive.
```
# cd /home/user/
# cp file1 /mnt/flashdrive
# cp file3 /mnt/flashdrive
```
To copy all the files from the directory instead of a select few do this:
```
# cp -r * /mnt/flashdrive
```
After copying all the files, check if the files have been copied ok by checking your flash drive from another computer.

HTH

---

### Post by JamezQ on 2010-03-06
Ok I am doing the commands to check disk space and i will list what I find.

First run, everything is normal except for a directory called ./var, witch has a whooping 273 G's.


Second run, there is a folder whiten var that contains 273G, it's name is ./backup.

Ok this is strange, when I try to navigate to backup, which has 273G's. 

It says: -bash: cd: backup: Permission denied

Certainly the problem must be clear now. I probably made a backup that kept backing up itself i'm guessing, my only question, is the fix clear, can I get my Ubuntu back or do i have to transfer data and reinstall?

---

### Post by JamezQ on 2010-03-06
[http://ubuntuforums.org/showthread.php?t=1422623](http://ubuntuforums.org/showthread.php?t=1422623)

This fixed it :) I have everything back now.

---

