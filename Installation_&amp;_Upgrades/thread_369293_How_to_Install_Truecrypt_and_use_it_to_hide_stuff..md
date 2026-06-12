---
title: "How to Install Truecrypt and use it to hide stuff."
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by humbll on 2007-02-24
This tutorial will show you how to install Truecrypt and use it to hide supersensitive files. In order for this to be even more secure, begin by following my tutorial on encrypting the entire file system which is located here:[http://www.ubuntuforums.org/showthread.php?t=293299&page=2]("http://www.ubuntuforums.org/showthread.php?t=293299&page=2")
This will ensure that your data never gets stored as plaintext on the swap partition or anywhere else. :)

To begin:
Step 0: Print these instructions.
Step 1: Click on this link:[ http://www.truecrypt.org/downloads.php]("http://www.truecrypt.org/downloads.php")

Step 2: Scroll down to the Linux section. From the dropdown menu select the file that matches your distribution. (Edgy is 6.10 x86 and Dapper is 6.06)

Step 3: Click download. Click Save File in the window that pops up.

Step 4: In the next window that pops up at the top of the list will be the file you just got. Click on the word OPEN next to it. A new window will come up showing you a file (called truecrypt-4.2a for Edgy) Double-Click that file. 

Step 5: You should now see 3 files: License.txt, Readme.txt, and truecrypt_4.2a-0_i386.deb
Doubleclick (truecrypt_4.2a-0_i386.deb)

Step 6: A new window will open, click INSTALL PACKAGE on the upper-right. You will be prompted for your password, type it and then press enter. The package will be installed and when it is done you will see the close button on the lower right side, click that.

Step 7: Now on the taskbar, click Applications-->Accessories-->Terminal
In the window that pops up type: **sudo chmod u+s /usr/bin/truecrypt**
You may be asked for your password, if so, type it and press enter.

Lets take stock: We have installed the program Truecrypt and in Step 7 we have given permission for all users to run it without having to use the "sudo" command and enter a root password each time. Now, the fun stuff. We are going to create a Truecrypt container within another Truecrypt container:

This next step creates our first truecrypt volume. the 110MB after --size tells it to make the container 110 Megabytes in size. you may, of course, make it smaller or larger if you like. You should make a guess as to how much space you need for storing files and double it plus add another 10%. So If you want to store 100 **Gigabytes** of data, 110% of 100GB is 210GB so you would replace the 100MB in the command below with 210**GB**.

Step 8: In the same (Terminal) window we were just using, type(or copy and paste):
[B]truecrypt --type normal --size 110MB -c volume.tc
[/B]
Step 9: Now you answer a series of options, first you will be asked what filesystem. Type the number 1 and press enter. This makes it a FAT32 filesystem.

Step 10: Select Hash Algorithm. Select either number 1 or number 3 and press Enter. (The second one was designed by the NSA, 'nuff said)

Step 11: Select Encryption Algorithm. Pick either 8 or 10 (these are three-in-one algorithms, first the data is encrypted with one, then the other, then the third. this is good in case a weakness is discovered in one you still have two layers of protection.)

Step 12: Enter a password for this volume. Select a good password or passphrase which uses  8 - 10 UPPERCASE LETTERS, lowercase letters, numbers, and special characters like punctuation. You will have to re-type the password to verify it. Here are some examples of decent passwords (in **bold** type): 
**My g00d password!** <--this one is secure because it uses upper & lowercase letters, spaces, and punctuation. Notice how I substituted zeros for the letter "o" in the word "good"

**$u$ans-$trong-Passw0rd!** <--notice how I substituted the dollar sign for the letter "s" in the words "Susan" and "Strong" also I used the same trick as in the first example by substituting a zero for the letter "o" in the word "password". You get the idea...

Step 13: enter keyfile path -->just press Enter

Step 14: Collect random data. Type **n** and press enter. ([COLOR="Red"]This step I could not use my mouse with (if you cannot use the mouse you will have to close the terminal window, open a new one and start over from step 8, so just use the keyboard to generate the random text for now.[/COLOR] Begin quickly typing jibberish include spaces numbers characters and upper and lowercase numbers, Shoot for about 10 - 15 lines of gibberish.

Now we are done with the first container, lets make the secret compartment inside of that one next. We want this one to be a little less than half the size of the first one. In our example above we used 110MB, so our secret compartment will be about 50MB:

Step 15: Type:
[B]truecrypt --type hidden --size 50MB -c volume.tc
[/B]
Step 16: Now you again answer a series of options, first you will be asked what filesystem. Type the number 1 and press enter. This makes it a FAT32 filesystem.

Step 17: Select Hash Algorithm. Select either number 1 or number 3 and press Enter. (The second one was designed by the NSA, 'nuff said)

Step 18: Select Encryption Algorithm. Pick either 8 or 10 (these are three-in-one algorithms, first the data is encrypted with one, then the other, then the third. this is good in case a weakness is discovered in one you still have two layers of protection.)

Step 19: Enter a [COLOR="Red"]DIFFERENT - Stronger[/COLOR] password than the one you used for the 1st container for this volume. Select a good password or passphrase which uses  20 - 35 UPPERCASE LETTERS, lowercase letters, numbers, and special characters like punctuation. You will have to re-type the password to verify it. Here are some examples of decent passwords (in **bold** type): 
**My $econd g00d password!** <--this one is secure because it uses upper & lowercase letters, spaces, and punctuation. Notice how I substituted zeros for the letter "o" in the word "good" and the dollar sign for the letter "s" in the word "second"

**$u$ans-$tronger-Pa$$w0rd!** <--notice how I substituted the dollar sign for the letter "s" in the words "Susan" and "Strong" also I used the same trick as in the first example by substituting a zero for the letter "o" in the word "password". You get the idea...

Step 20: enter keyfile path -->just press Enter

Step 21: Collect random data. Type **n** and press enter. ([COLOR="Red"]This step I could not use my laptop mouse with (if you cannot use the mouse you will have to close the terminal window, open a new one and start over from step 8, so just use the keyboard to generate the random text for now.[/COLOR] Begin quickly typing jibberish include spaces numbers characters and upper and lowercase numbers, Shoot for about 15 - 25 lines of gibberish.

Now that we have made our outer container with our secret container within it, it is time to put it to some use. First thing we do is put some files into the first container to throw off a would be snoop. That way, if they beat you or imprison you to compel you to tell them the password, you can give them the password to the **first** container. [COLOR="Red"]NEVER would you want to give them the password to the hidden compartment or even let on or admit that it exist[/COLOR]s or else an enemy could beat the password out of you or the courts could throw you in jail until you give them the password!! There is no way that they can even tell there is a hidden compartment - the **ONLY** way they will know is if you tell them!! so anything you put in the hidden compartment is totally safe!! For now, lets put some decoy files in the first container. You can place a few MP3's in in, along with some sensitive looking data. Anything to throw them off... If you were implementing this for real, you would put any semi-sensitive stuff in here, stuff it would be Ok for someone to find but that you could easily pretend you did not want anyone to see. Use your imagination...(maybe a series of porn pics you can claim you didn't want the wife or kids running across, whatever, as long as you can make it sound believeable)...

Step 22: We will place the file you downloaded earlier into the first compartment, but first we will rename it to make it a bit easier on us... this assumes you used the Edgy version if yours was different substitute the name of the file you actually downloaded for the filename used below (as an alternative you can click Places-->Desktop  then right-click the file you downloaded and rename it to:  tc.tar.gz):

Type in the terminal window:
**cd /Desktop**     then press Enter
Then type (or copy & paste):
**mv truecrypt-4.2a-ubuntu-6.10-x86.tar.gz tc.tar.gz**  then press Enter
This renames the file from the long name it had to the name** tc.tar.gz**
Now to move it into our 1st container:

1st we create a mount point for the container, type:
**sudo mkdir /mnt/tc**   press Enter and give the system password if asked.

next we mount the 1st container while protecting the hidden container within, type:
**truecrypt -P volume.tc /mnt/tc**  and press Enter. Note the capital -P not -p in the command
Here you will be asked for the passwords for each container in turn, supply them.

now the transfer of the dummy file, type:
**sudo cp tc.tar.gz /mnt/tc**     and press enter - give the root (system) password if asked for it.

Now to recap what we just did:
We mounted  the outer container then transfered our dummy file to it. now we will unmount the outer container, type:
**truecrypt -d**

Now we shall mount our hidden secret container and put some pretend secret data on it, type:
[B]truecrypt /root/volume.tc /mnt/tc
[/B]
It will now ask for the volume.tc password. Type in the password to the secret compartment (from step 19) and press enter. If we were to enter the other password here, it would mount the outer container but without protecting the hidden one. There is no more use to mount the outer container anymore once it contains the dummy data, except maybe to access the data once in a while to make it look like we are actually using it. But you would be wise to use the command **truecrypt -P volume.tc /mnt/tc** instead when doing this so as to protect the hidden volume within from being destroyed when you want to access the data in the outer volume. Onward:

Our secret compartment is now mounted and we can put our secret data inside:
type **sudo mv tc.tar.gz secret_data**   and press enter. supply the root password if prompted. (we are making the file you downloaded and renamed into our secret data file now)

Now we move the secret data to the hidden container, type:
**sudo mv secret_data /mnt/tc**  and press enter. supply the root password if prompted.

Now our secret data is in the hidden compartment. So we unmount the secret compartment now so no one stumbles upon it,  type:
**truecrypt -d**  and press enter

 Remember, If ever you want to work on the secret data files, use this command to mount the hidden compartment:
**truecrypt /root/volume.tc /mnt/tc**  and give the password to the hidden compartment.

If you want to acces the outer compartment to play with the data in it without possibility of destroying your secret files on the hidden compartment, use the command:
**truecrypt -P volume.tc /mnt/tc**   and give each password in turn, first the outer, then the hidden compartments password.

And if an enemy demands the password to the encrypted volume, supply them ONLY with the OUTER compartments password. If they make you mount it for them you would use the command:
**truecrypt /root/volume.tc /mnt/tc**   and use the outer compartments password. This leaves the hidden files vulnerable to being destroyed but they are at least safe from being discovered.

And that is it! To reinterate: if you are compelled to supply a password to an enemy simply provide them with the OUTER containers password, they will only be able to access your dummy data and the real secrets are safely tucked away. If they play around with things too much they may end up destroying the secret data, but at least they will never get their grubby little hands on it!! [COLOR="Red"]REMEMBER: NEVER EVEN ADMIT THAT THERE IS A HIDDEN CONTAINER WITHIN THE OUTER ONE, there is absolutely no way they can tell there is one, so the only way they would find out is if YOU tell them![/COLOR] Loose lips sink ships...

There is much more you can do with Truecrypt, check out the documentation for the Linux version you downloaded by following this link: [http://www.truecrypt.org/docs/linux-manpage.php]("http://www.truecrypt.org/docs/linux-manpage.php")

I will be cleaning this up a bit but for the most part it should be found to be adequate.

---

### Post by fakie_flip on 2007-03-04
> **humbll said:**
> 
There is no way that they can even tell there is a hidden compartment - the **ONLY** way they will know is if you tell them!! so anything you put in the hidden compartment is totally safe!! 
...
If you want to acces the outer compartment to play with the data in it without possibility of destroying your secret files on the hidden compartment, use the command:
**truecrypt -P volume.tc /mnt/tc**   and give each password in turn, first the outer, then the hidden compartments password.

And if an enemy demands the password to the encrypted volume, supply them ONLY with the OUTER compartments password. If they make you mount it for them you would use the command:
**truecrypt /root/volume.tc /mnt/tc**   and use the outer compartments password. This leaves the hidden files vulnerable to being destroyed but they are at least safe from being discovered.


If someone looks through your ~/.bash_history and sees that you did the command below with the -P option then he or she will know you have a hidden volume.
```
truecrypt -P volume.tc /mnt/tc
```

---

### Post by cubanresourceful on 2007-03-04
Thanks for the wonderful guide, and I love the end part about enemies and such. Now I can hide my "collection" from prying eyes. :D

---

### Post by fakie_flip on 2007-03-04
I'd like to use ext2 or ext3 filesystem on a normal (not hidden) truecrypt volume, but I am getting errors from trying that.

```
chris@ubuntu:~$ truecrypt -u chris.tc b
Enter password for '/home/chris/chris.tc': 
mount: wrong fs type, bad option, bad superblock on /dev/mapper/truecrypt0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

truecrypt: Mount failed
```

Here is the last line from dmesg.

```
[17239115.896000] truecrypt: no version for "struct_module" found: kernel tainted.
```

---

### Post by fakie_flip on 2007-03-04
Just beware that if someone is using lkl (Linux KeyLogger), that he or she can get your pass phrase. I run chkrootkit once in a while.

---

### Post by nami on 2007-05-08
> **fakie_flip said:**
> If someone looks through your ~/.bash_history and sees that you did the command below with the -P option then he or she will know you have a hidden volume.
```
truecrypt -P volume.tc /mnt/tc
```

how do you get around this problem?

> **fakie_flip said:**
> Just beware that if someone is using lkl (Linux KeyLogger), that he or she can get your pass phrase. I run chkrootkit once in a while.

i thought linux couldn't get infected with stuff like this???

---

### Post by fakie_flip on 2007-05-08
I tested lkl on a few computers. It doesn't work with usb keyboards, so I am safe from it, only ps/2 keyboards. Stuff like this is rare, but there is chkrootkit and clamav. This is the only keylogger for Linux that i have heard of. Whenever you run gksu, it freezes all other apps or grabs the mouse and keyboard, so other applications can't read your password.

---

### Post by fakie_flip on 2007-05-08
lkl is actually in the repos. just do this to see what i mean.

apt-cache show lkl

---

### Post by fakie_flip on 2007-05-08
of course people can run sniffers on your computer too to see anything you are sending over the internet that isnt encrypted

---

### Post by fakie_flip on 2007-05-08
> **nami said:**
> how do you get around this problem?



i thought linux couldn't get infected with stuff like this???

I'm not worried about it too much because I don't think anyones going to force me to give them my password for truecrypt, and that i have to hide a hidden one inside of the first one. theres a way to disable bash history. ill give you the guide.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_disable_history_listing_in_Console_mode](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_disable_history_listing_in_Console_mode)

---

### Post by Mack1 on 2007-05-08
erm....i'm in serious need of help....no....not me....but my ubuntu :-)

I followed humbll's guide (good one!!) and did everything exactly as he said.

However, everything goes well up untill i create a volume. this works ok.
But when i try to mount if the fun starts :(

info: i changed owner and group of /usr/bin/truecrypt to my user instead of root to change
access permissions and stuff.

it says:

insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.20.ko': -1 Invalid module format
FATAL: Module truecrypt not found.
Failed to load TrueCrypt kernel module

i've also had once or twice (but not the problem atm):

"Failed to assign loopback device for file-hosted volume"

I've tried loads of google searches but i can't figure out what to do now.

Is there someone who can help me?

I'm a bit of an ubuntu rookie, have only tossed away my winxp for a couple of months so please
try and ignore my ignorance :lolflag:

---

### Post by fakie_flip on 2007-05-11
What did you do to get that error?

---

### Post by Mack1 on 2007-05-11
Hi,

I tried to mount the volume i created.

Followed everything to the letter but when i try to mount the volume
bang! this error occurs :(

any idea?

i'm at a loss....

---

