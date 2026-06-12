---
title: "[SOS] Can't stop installation from encrypting home folder"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by gnomeout on 2010-06-11
Hey,

I have a CD image for 10.04 lucid lynx 64-bit. I have used it to install Ubuntu twice now. The first time everything went fine. But the second time my home folder got entirely encrypted which was not fun at all, and definitely didnt happen the first time! I didn't even realize it till I had to investigate why everything was going so slow on my system!

ANYWAY here is my problem:

I went to do ANOTHER clean install with the same CD and noticed where my problem came from. The installation CD is encrypting my home folder and giving me no say in the matter. When I get to the screen(during installation) where I enter my name and password, the options at the bottom are greyed out. I cannot select automatic login or change it in any way, it is permanently stuck on "enter password to login and decrypt home folder" which leads me to conclude that it has just enabled home folder encryption without my permission!!!!

I tried removing ecryptfs-utils from the live boot, but then it wont let me launch the installation program at all! 


What do I do??? I went online searching and NOONE else seems to have this issue. there are tons of guides online for installation and they all say that when this screen comes up you can select any one of the three options... WHY CANT I???!!


kthxbye

---

### Post by gnomeout on 2010-06-11
Also I am trying downloading a new CD image for both 64 and 32 bit versions to see if either of those work, but it takes an hour per CD image on my incredibly slow internet connection :( wont be available to test them till tomorrow, so your immediate help would still be greatly appreciated.

---

### Post by pricetech on 2010-06-11
I don't believe it's possible for the install disk to skip your input like that.  If it did you wouldn't even have a place to put in a username.

---

### Post by gnomeout on 2010-06-11
Not sure what you are referring to. It is not skipping anything by the looks of it. I see every screen. But I am never asked if I want to encrypt my home folder at any point. Then when I get to the login information screen, all my options are greyed out.....

At no point am I given the opportunity to input anything to any other effect... and I am not making this up... So I am not sure what you are trying to tell me with your post...??

I will make a screenshot walkthrough if my issue persists after trying with these new images. Going out for tonight though.

---

### Post by pricetech on 2010-06-11
When you are prompted to enter a username and password, there is an option to password protect your account or password protect and encrypt your stuff.

That's my best recollection.  It's been a week or so since my last install and I've had a lot of other projects on my mind so I could be remembering wrong.

I do remember the two options, just not positive that's the screen where they show up.

---

### Post by darkod on 2010-06-11
> **gnomeout said:**
>  the options at the bottom are greyed out. I cannot select automatic login or change it in any way, it is permanently stuck on "enter password to login and decrypt home folder" 

The OP already stated the problem, he can't select anything but encrypted home folder. But I have no idea what could be the problem and how to fix it.

---

### Post by pricetech on 2010-06-11
I see that now.  I must have misread it the first time around.  It almost sounds like someone made a custom CD.  I don't know of any "corruption" that could take that choice away.

OP: Are you trying to reinstall over the top of the earlier installation or are you wiping it out and doing a fresh install ??  If the former, then it's picking up settings from your existing install.

---

### Post by gnomeout on 2010-06-12
Hey, thanks for replies. Yes it seems super odd to me as well. 

Yes, I am installing it over a pre-existing installation, but I am formatting the root filesystem... here is exactly what my setup is.

I have a 20GB filesystem for my root folder and core filesystem. Then I have a 400+GB partition for my home folders, entirely separate. 

When I go to install I tell it to format the 20GB partition and install fresh on that one after formatting!
 
But I do not format my home partition (the 400+GB) because that has my files backed up on it(which I copied out of my home folder so they are not encrypted which is the whole reason I am reinstalling). So formatting this partition is pretty much not an option... :(

I am not prompted at any point to use settings from my previous ubuntu installation, so it seems weird that it would just detect my previous encryption and "assume" that I want it again. Are you sure this is possible, pricetech? Because I am prompted later to import settings from my windows 7 installation(which I always deny anyway) but it never offers any sort of setting import for my previous ubuntu installation.

BUT if this were actually my problem, how would I get around it without formatting my home partition???


I just got in the door and am going to sleep now, will post in the morning with success/failure of my newly downloaded CD images. 

Thank you everyone for you help, and thank you in advance if you have any more solutions/suggestions for me in the meantime.


Night.

---

### Post by gnomeout on 2010-06-12
Ok, new image made no difference, my problem is exactly the same.

Pricetech, so far your suggestion that it is picking up my previous encryption settings is the only one. And it makes some sense since my last installation(the one that encrypted my home folder) was my first installation since installing ecryptfs for just the private folder (the individual folder rather than encrypting my whole home folder). Since that point of installing ecryptfs is when this seems to have started happening. Any suggestions to fix it??? I dont want to just remove ecryptfs from my actual installation only to find I need to do more, cause then I will be without a home folder on my computer to even boot into(since it would be encrypted and I would not have ecryptfs).


And I will reiterate that this is super lame of ubuntu if this is actually happening... Should I report a bug...? Gah!

I am lost... considering buying a new hard drive just so I dont have to deal with this anymore... then I could just use the new drive for my home folder and presumably it would not detect/enforce any encryption....?  FML



I have the screen shots attached here too... not that they will really be that informative.. I left out the first three screens since there is a limit on the number of screenshots, but they are only Language Selection, Time Zone selection, and Keyboard Map selection, so nothing vital....

Screenshot-5 is the money shot... Thats the middle thumbnail in this post. It shows the greyed out options.

---

### Post by gnomeout on 2010-06-12
Ah, here are the first three, unimportant, screens. For your viewing pleasure.

Glad I can add more attachments for every post.

---

### Post by pricetech on 2010-06-13
If you're keeping your home folder unformatted, it might be picking up a "tag" of some kind that causes it to be encrypted.  That's a theory based upon what you've told us.

You might have found a bug, but I can see where it could be considered a security feature also.  For example, you have your home folder encrypted for whatever reason, someone gains access to you machine and installs a second instance of the OS to gain access to your data, the feature keeps that from happening.

I don't know that I would say that makes sense entirely because it's pretty much accepted that if someone gains physical access, your stuff it toast anyway.  With the proliferation of laptops, and the relative ease, and greater likelihood of loss or theft, it might keep your data from being compromised.

Again, this is a theory since I haven't read up on the subject.  I'll make a "note to self" to look this up sometime.

As a workaround;  Can you access your stuff from a live CD, decrypt it, and copy it to another location unencrypted ??  If so, you could then wipe home and do away with the encryption.  A pain I know, but it may be your only option at this point.

---

### Post by gnomeout on 2010-06-13
Well thats not exactly whats happening... but it could be close..

You see before I go to reinstall I rename my old home folder so that I will get a new one. And I also renamed the ".ecryptfs" folder which is where all the encrypted files are. I renamed this in an attempt to prevent the install CD from detecting that I had encryption. 

And like I said before, I copied everything out of my home folder into an unencrypted folder already. It would be crazy to reinstall and think i would still have access to my encrypted home folder, I would definitely need to use the encryption key(and not the passphrase) to recover my data if I did that. 

This also does not make sense as a security feature in the scenario you describe because if someone did that and installed a second OS to "access my files" all they would see is my home folder which would appear empty except for a README and some other file telling you that the contents are encrypted and you cant access them. The other thing they would see if they were smart enough to look is the hidden ".ecryptfs" folder which would have all the encrypted data and be pretty useless without the encryption key. So this doesnt really work as a security feature; the whole point of encrypting the home folder is to prevent someone accessing your files should they ever get physical access to your drive. 

Thanks for trying to help anyway though. much appreciated. I've posted the same question on Launchpad and so far nothing there either... buying a new drive is looking better and better....

---

### Post by darkod on 2010-06-13
I'm not experienced at all with encryption but I think it's detecting this encryptfs and that's why it offers only that option during the new install.

---

### Post by gnomeout on 2010-06-13
> **darkod said:**
> I'm not experienced at all with encryption but I think it's detecting this encryptfs and that's why it offers only that option during the new install.

Yes that seems to be fairly certain based on the circumstances...

Now I am trying to find ways to prevent it from detecting ecryptfs without having to wipe my home partition... Or do you think it could be detecting it on my root partition?... Hmmm I am going to do some experimenting on my live CD try switching the partitions mounting points... and try a few other things... maybe.....

---

### Post by gnomeout on 2010-06-13
OK, problem solved. It was an obvious solution, but one I was hesitant to try since it would have been irreversible. 

Putting it simply, delete everything encrypted... 
Specifically I removed both my home folder(which is pretty much empty anyway since its encrypted) and the .ecryptfs folder (where the actual encrypted files are).

I am not sure whether just one, or both of these need to be removed, but there you have it. Thats what I did.

Also, I copied these folders to an external drive before deleting them, so I can recover my data (with the encryption key) if I realize I forgot something. But there is one file in the .ecryptfs folder which is special and cannot be moved or copied. I actually left this on my home partition without deleting it. This way I can copy everything back into place when I am done reinstalling and nothing will be damaged.

I would NOT recommend deleting this special file if you want to be able to access your encrypted files later. Keeping it will not mess up the installation like before. But if you have backed up everything OUTSIDE your encrypted folder and are sure you no longer need anything to do with encryption then go ahead and delete it.


Hope this helps other people...

---

### Post by prokher on 2010-12-06
Thank you guys I faced this problem too, and this thread helped me a lot.

---

