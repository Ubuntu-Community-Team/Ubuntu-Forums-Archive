---
title: "New installation, need to get access to previous home folders."
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2012-04-27
Hello everyone :)

I just installed 12.04 on my sister's in law computer.
This computer is used by the whole family, and it had 10.10.
Since support is over for the 10.10 I decided to upgrade to 12.04.

Unfortunately upgrade to 11.04 failed and it rendered this computer inoperable.  So I did a fresh install on 12.04.

I have a / partition and a /home partition.
I formatted the / partition but I left the /home partition intact.
On the /home partition there are 5 different directories, each one for the 5 members of the family that is using this computer.

My question is this...

How do I regain access to the directories for each user, when I create for each one their new accounts?

Thank you all in advance

[edit]

One more question on this.  the / partition is formatted with ext4 but the /home directory is formatted with ext3.  Is there a way to upgrade /home to ext4, without loosing all the data?  (other than backing up and reformatting).

---

### Post by dFlyer on 2012-04-27
Just recreate the user using the same name as before.

---

### Post by AzzMG on 2012-04-27
I belive it is best to open one nautiluswindow via sudo. then browse the old folders and move them to your newly made folders.

You might need to chown them afterwards.

---

### Post by papibe on 2012-04-27
Hi Ifaistos.

There are several ways to accomplish that, but this what I would do (jsut being extra safe):

Before creating any user, move the directories to a safe place:
```
cd /home
sudo mkdir oldusers
sudo mv -iv user1 user2 user3 user4 user4 oldusers
```
Then I would create the users as they were new.

Finally, I would restore their files. For instance, for user1:
```
sudo rsync -avx /home/olduser/user1  /home/user1/
```
(same structure for every user).
I'm using rsync instead of 'mv' or 'cp' because it' safer. If something goes wrong, you just run the rsync command again.

Once you can make 100% your users have their data, you may want to erase the olduser directory:
```
sudo rm -rf /home/oldusers
```

Caveat: the way I'm suggesting requires space to copy the files. If you don't have the space, use 'mv -iv' instead of the rsync command.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by hno3 on 2012-04-27
Step 1 - After you do the fresh install in the partition where you had the / earlier, create a new admin user which does NOT have the same name as any one of the 5 family member user names.

Step 2 - This newly created user in the fresh installation would be placed in /home/newuser but in the / partition and not in the /home partition that you had created earlier. So in step 2 move the home to the new partition. Use the guide @ [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome") to move the home to the other partition. At the end of step two your system looks like this:-
[A] One user that we created
[B] Two partitions /root in one and /home in other
[C] In the home partition there are six folders one is newuser folder and other 5 are your family member's homes from previous installation.

Step 3 - Create 5 user accounts for your 5 family members and all your docs and data would still be intact.


Note: I'd still recommend backing up data.

---

### Post by Ifaistos on 2012-04-28
Hello everyone and thanks for all the suggestions.

Before I try anything I would like you to consider the following and tell me whats your suggestion.

I am under the impression that in Linux, security is file based.
So if for example I recreate users with exactly the same names as before the directories will be the same, and normally I would be able to have access to the files in the home folders of each user from the previous installation... if I were in windows.....

Now that I am in Linux (thank god!!) would I be able to have access (read and write) to those files?  Will Linux be able to recognize those files as my own.. or as the new user's files?

If this is the case then this might be a security consideration for Linux.  Think of this...

I want to hack into someone's computer.  I go to his computer and check out his username.  That's all I need....  I re-install Linux, and create a new user, with the exact same name of the old user.  If Linux sees the new user as the owner of the files in the directory, then all it took for me to "break" the security of Linux, was just half an hour it took to reinstall Linux.

These are my thoughts... 
I am not sure if this is the case.  I don't know if the solution is as simple as recreating the users with the same names as before.  If it is... then I am ok with that... If it's not.. then please consider that thought in your solutions.

I believe that the whole think is how to make Linux recognize the new user as owner of the file of the old user.

I hope I didn't confuse anyone.
Thank you guys :-)

---

### Post by darkod on 2012-04-28
You mentioned in your first post that you have a separate /home partition but never mentioned exactly did you use it in the last install or not. I guess you did tell the installer to use it and it mounts OK in your new install.

If that is correct, you can simply create new users using the existing home folders with:
sudo adduser --home /home/username username

In most cases that will take care of permissions and ownership. In case it doesn't, you can:
sudo chown -R username:username /home/username

It's that simple instead of copying and moving stuff around.

As for the security questions, I don't know. You can open a thread about that in the Security section if you want to get more detailed information. As far as reusing existing home folder is concerned, the command above will work just fine, I have the same setup with separate /home.

---

### Post by Cheesemill on 2012-04-28
> **Ifaistos said:**
> If this is the case then this might be a security consideration for Linux.  Think of this...

I want to hack into someone's computer.  I go to his computer and check out his username.  That's all I need....  I re-install Linux, and create a new user, with the exact same name of the old user.  If Linux sees the new user as the owner of the files in the directory, then all it took for me to "break" the security of Linux, was just half an hour it took to reinstall Linux.

No need to even do that.
Just boot with a Live CD and you have access to all the files on the hard disk (unless they have been encrypted).

As has been said countless times before:
Physical access = Root access

---

### Post by Ifaistos on 2012-04-29
Thank you all for your suggestions.
This is the result I get from trying to create one of the users
==============================================================

The home dir /home/amarilis you specified already exists.
Adding user `amarilis' ...
Adding new group `amarilis' (1001) ...
Adding new user `amarilis' (1001) with group `amarilis' ...
The home directory `/home/amarilis' already exists.  Not copying from `/etc/skel'.
adduser: Warning: The home directory `/home/amarilis' does not belong to the user you are currently creating.
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for amarilis


[edit]
The chown command worked perfectly.
Tell you the truth, this is exactly what I expected from Linux.  I would be dissappointed if it would allow me to see the files right from the beginning without chown.

Thank you all!!

Marking this as solved :-)

---

