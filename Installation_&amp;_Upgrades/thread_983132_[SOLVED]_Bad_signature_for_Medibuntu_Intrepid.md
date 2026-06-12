---
title: "[SOLVED] Bad signature for Medibuntu Intrepid"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by Maelgwyn on 2008-11-15
Hi guys,

Recently when running any apt-get, the following error crops up:
```

A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://packages.medibuntu.org intrepid Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>

W: Failed to fetch http://packages.medibuntu.org/dists/intrepid/Release 

```

I've tried using the instructions on the Medibuntu post (I even copy-pasted to make sure I wasn't mis-spelling things), but the error still happens.

Anybody else getting this?

---

### Post by Maelgwyn on 2008-11-20
Nobody? *bump*

---

### Post by Partyboi2 on 2008-11-20
Open a terminal and try adding the key again[FONT=monospace]
[/FONT]```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by Maelgwyn on 2008-11-20
I've tried that :(

---

### Post by Partyboi2 on 2008-11-21
Is there a key for medibuntu listed in Software Sources under "Authentication" If there is try remove it then re adding the key.

---

### Post by Maelgwyn on 2008-11-21
Gave that a go, but get the same error:

```
Fetched 190B in 1s (154B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: Failed to fetch http://packages.medibuntu.org/dists/intrepid/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

---

### Post by mc4man on 2008-11-21
What you want to do is to re install the medibuntu-keyring package, The easiest way would be to search it in synaptic, mark for Reinstallation and apply. 

If that doesn't work post back, it that case you may need to remove it, but there is  something you'd need to do first.


edit : note that running the wget will not cause a reinstallation

---

### Post by Maelgwyn on 2008-11-23
I tried the reinstallation option through Synaptic, but got the same error as soon as I refreshed =/
I'm tempted to just remove the medibuntu source etc

---

### Post by mc4man on 2008-11-23
If you want to give a try to removing everything there are probably 4 files, (2 files, 2 shell scripts), 1 key file and the package.

Why don't you first ck. something else. Did you ever manually enter the medibuntu sources in preferences -> software sources -> third party? 

Run this to ck. (if there are medibuntu entries you did

```
cat /etc/apt/sources.list
```

Edit: 
this is what I'd do

If there are any entries /etc/apt/sources.list,  then delete them. Having both manually entered sources and using wget for the same can cause issues.

```
gksudo gedit /etc/apt/sources.list
```

Run gksudo nautilus and navigate to /usr/share/keyrings and delete the medibuntu-keyring.gpg file

Navigate to /etc/apt/sources.list.d/ and delete the medibuntu.list inside (and the backup - medibuntu.list.save

Open up synaptic, search medibuntu and mark the medibuntu-keyring package for complete removal, click apply

This should also remove the 3 files in /var/lib/dpkg/info

Now run (this is for intrepid as per thread title

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

and then

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

I'd be very surprised if everything wasn't squared away

---

### Post by Maelgwyn on 2008-11-23
Really hates me! I've gone through and deleted everything like you wrote and when I run apt-get update:
```
Fetched 190B in 1s (151B/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: You may want to run apt-get update to correct these problems
nik@tangata:~$ 

```This is beginning to just get funny...


Going to try changing from NZ servers to "main" server, to see if that helps anything.

*edit* No such luck. =(

---

### Post by mc4man on 2008-11-23
I'm not on my machine atm but it is very curious.
If you look closely at your error messages you'll see you started with a "badsig". 

After removing the key and running the wget you got a "NO_PUBKEY" which would be expected since the keyring package was already installed and that command doesn't reinstall the package (ie. the key file

Then after removing the package ect.and doing a fresh install your back to "badsig"

Did you find entries in sources.list?

Edit: 
When you tried running the wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update line after removing everything it should / would have come to a prompt saying blah, blah couldn't be authenicated or something to that effect.
You would have had to enter Y or n to continue.

Do you remember that happening and did you answer Y

---

### Post by nwstephens on 2008-11-24
I'm having the same problem, except I can't even find any medibuntu packages (including the keyring) in the package manager.  I'm just coming off a fresh install of Ubuntu.  I've added the medibuntu repository about a dozen times with no problems...until now.

After removing all pertinent files mentioned by mc4man and running the two standard commands I get the following error:

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

---

### Post by breandan_anraoi on 2008-11-24
I have had exactly the same problem as mc4man since I added medibuntu. I did exactly as instructed on the medibuntu page, I followed all the commands advised above, and I'm getting exactly the same errors.

---

### Post by waydownsouth on 2008-11-24
+1 for the identical error, even after manually deleting everything and starting from scratch as prescribed earlier.

Its been going on for at least a week (more like 2), I initially thought it might be to do with server loads from the release of intrepid and have ignored it in the meantime.

no such luck it seems...

---

### Post by mc4man on 2008-11-24
Well I've purposely 'broken' this multiple times and fixed it no problem  by simply reinstalling the medibuntu-keyring in synaptic. (with the error "The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783"

I can't seem to get the error "The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>" but I  have an idea about that I'll try later.

What are you all using, 32 bit or 64 bit? (looking for something in common. I have a 32 bit install

Did any of you show entries for medibuntu in sources.list

```
cat /etc/apt/sources.list
```

And as I edited in last post if starting 'fresh' and then re running the wget lines you will come to a prompt where you have to answer y or n. If that doesn't occur then the keyring and key weren't removed. (and you have to answer yes

---

### Post by waydownsouth on 2008-11-24
32 bit here,

no entries in sources.list,

answered yes to reinstall.

---

### Post by mc4man on 2008-11-24
I'm probably missing something here but lets try this.

Go to system -> admin.. -> software sources -> authentication and see if there is an entry for medibuntu.
If so highlight and remove and for good measure, click restore defaults.

Then search medibuntu in synaptic, mark for reinstallation and apply.
After that in terminal go sudo apt-get update and see.

If there's anything of the above you can't do post what it was.

---

### Post by waydownsouth on 2008-11-24
all done & still have the BADSIG error,

I marked for complete removal first, then reinstalled.

---

### Post by oldos2er on 2008-11-24
This worked for me: 
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---

### Post by mc4man on 2008-11-24
If you getting the badsig vs public key not avail... I can't seem to create that situation.
Which one are you seeing

If you could do a removal then there was no medibuntu-keyring.pgp in /usr/share keyrings. It is created as a result of installing medibuntu-keyring (after that it's presence is not needed


Edit ; if your getting the cannot auth.....no public key avail. then it really doesn't matter in terms of using medibuntu, it just means it's not being authenticated, nothing more.
Watching in /var/lib/apts/list while running an update all of the medibuntu package lists are recreated just fine. The only thing missing is the medibuntu.....Release.gpg which really doesn't matter.( can't see why  any of the mentioned ways don't 'fix' that, ultimately it doesn't really matter

If your getting the error in post one (failed to fetch) then probably just removing the entry in admin.., software soueces, auth... will resolve to the above.

---

### Post by waydownsouth on 2008-11-24
Still the same...

Its more of an annoyance with update manager giving the error repeatedly when there seems to be no good reason why it would. 

Ever since I did the jump to intrepid via upgrade manager my whole system hasn't quite been right, I guess this could be another bug related to the upgrade?

Oh well,
I see a fresh install in my future.

---

### Post by nwstephens on 2008-11-26
Ditto.  After upgrading to Intrepid via the update manager I've experienced nothing but bugs.  I completed a reinstall which fixed most issues, but left me with this problem of being locked out of Medibuntu.  I've tried all of the advice in this thread to no avail.  I can't even get medibuntu to show up in the package manager search.  I think it's time for yet another reinstall.

---

### Post by mc4man on 2008-11-26
the medibuntu-keyring package only shows up in synaptic after medibuntu is added as a source and or if you've installed it with a wget command.

If you were to run this, medibuntu is added

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

this installs the keyring for authentication which isn't necessary to download packages, without it you'll just have to answer 'yes' to installing without authentication.

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

You could try both or just do  the first one followed by 
```
sudo apt-get update
```

If you get unable to authenticate that doesn't really matter, a failed to fetch obviously does.

---

### Post by Maelgwyn on 2008-12-01
I've tried your suggestions there mc4man, but still no luck >.<

---

### Post by kogos on 2008-12-19
I had exactly the same problem as you do m8, and luckily, i just found the solution... 

open a terminal/konsole, and type: 
```
sudo apt-get remove medibuntu-keyring
```
This will give you an error... then type it again, exactly the same command, and this time, it will remove the keyring.... Now, check your software sources and you'll see that there is no medibuntu authentication in there..... 

Now, type 
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
and 
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

During the first apt-get update, you will get an error, but that's normal... however, it will not pause or stop the installation of the medibuntu-keyring... and you should be as good as new:)

Let me know if that worked or we can figure something out!

---

### Post by Maelgwyn on 2008-12-19
I could kiss you! just updated and there's no error message! =D

---

### Post by kogos on 2008-12-20
glad i helped... it's sad that adept is still beta though:( That made me dump kubuntu, and i only use it to test things and reproduce/check bugs from launchpad

---

### Post by d0.higgs on 2010-07-03
Thank you "kogos", this really helped me with lucid.
I had to change intrepid to lucid in the url, and all went fine.

d0.higgs

---

