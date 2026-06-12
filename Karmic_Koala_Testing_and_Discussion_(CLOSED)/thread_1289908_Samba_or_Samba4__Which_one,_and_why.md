---
title: "Samba or Samba4?  Which one, and why?"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-12
Just because I see both in the repos, I am kind of curious.

---

### Post by iamhugeinjapan on 2009-10-12
Samba4 is experimental still. So if you don't know what it is then you're probably best to stick with Samba. But if you're in the Karmic forum then maybe you want to live life on the Samba4 edge, but don't use it for critical shares.

---

### Post by cariboo on 2009-10-13
Samba4 has a lot of cool things coming, have a look [here]("http://wiki.samba.org/index.php/Samba4"), but as iamhugeinjapan said, it's not ready for prime time yet.

---

### Post by psyke83 on 2009-10-13
The main selling point will be that [Windows Server will now join, trust and replicate a Samba-based Active Directory using Microsoft-native protocols.]("http://people.samba.org/people/2009/10/05#drs-success").

Also see the [Slashdot article]("http://tech.slashdot.org/story/09/10/10/1818249/Windows-Server-Trusts-Samba4-Active-Directory?art_pos=7").

---

### Post by emarkay on 2009-10-13
Cool thanks.

But still no "Network Wizard" for "one cliick XP Jaunty, Karmic, Vista, OS X and Amiga (heh heh heh) detection and configuration?    

That's the pimple-pus in Ubuntu so far - all the CLI that needs to be done to network - almost like Window$ before "plug and pray" was in 1994 or so...

---

### Post by danwood76 on 2009-10-13
meh CLI is great.
Point and click = disaster!

Mind you there are some nice GUIs for samba config if you look.

---

### Post by cb951303 on 2009-10-13
> **emarkay said:**
> Cool thanks.

But still no "Network Wizard" for "one cliick XP Jaunty, Karmic, Vista, OS X and Amiga (heh heh heh) detection and configuration?    

That's the pimple-pus in Ubuntu so far - all the CLI that needs to be done to network - almost like Window$ before "plug and pray" was in 1994 or so...

what exactly do you need?

nautilus automatically detects samba shares and you can right click and share a directory without pain.

---

### Post by emarkay on 2009-10-13
> **cb951303 said:**
> what exactly do you need?

nautilus automatically detects samba shares and you can right click and share a directory without pain.

I keep reading about having to adding your "workgroup" name (which I have) , and some  other information one needs to configure in /etc/samba/smb.conf. 

Regardless, in all these years I have never been able to interconnect my 3 or 4 PC's of varying configurations in Ubuntu.  Yes I have a folder that is marked "Share" in all. 

It would be nice to not have to "sneakernet" USB sticks around the home in Ubuntu, although it has never (honestly) been important enough to really spend a few hours to debug...

Edit: I see that there has been some big changes to the "instruction manual"  Looks like there is now less CLI needed...  Will investigate,
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Thanks.

---

### Post by Jerry N on 2009-10-13
Am I missing something here?  I have a mixed network of Ubuntu, Win XP and Win 7 and, at least with Ubuntu 9.04 and 9.10, I don't need any CLI.  Am I doing something wrong? 

I did need to mess with a Samba configuration file back in 7.04 or 7.10.  

Jerry

---

### Post by nanog on 2009-10-13
Or you could switch to NFS which is 2-10x faster and hundreds of times more stable.

---

### Post by Roasted on 2009-10-18
> **nanog said:**
> Or you could switch to NFS which is 2-10x faster and hundreds of times more stable.

In my experience, NFS isn't significantly faster than Samba to be worth bragging about, and I've never had an issue with Samba's stability - ever. And secondly, I was aware that Samba was the only way to network multi platforms, whereas NFS is linux only. Is this still true?

---

### Post by solnyshok on 2009-10-19
I played yesterday with IIS7.0 on my Window7 machine, and noticed that there is an option to install NFS support for connection to Unix machines. (under control panel, programs, manage windows components)

I did not try it, since my home network is still on SMB/Samba.

---

### Post by mikedep333 on 2009-10-19
Guys, keep in mind three things:
1. Samba 4 is clearly labeled as in Alpha in the repos. You do not want to use it yet.
2. Nautilus includes a GUI for sharing folders. Just right click on the folder icon and go to sharing options.
3. If you want to override the smb.conf, you can, and that's how you specify a workgroup other than "workgroup". Just keep in mind that it will prompt you to overwrite it every time there is a (security) update to samba.

---

