---
title: "NO_PUBKEY ... update failed :("
date: 2016-05-24
forum: Installation &amp; Upgrades
---

### Post by hawaii243 on 2016-05-24
Something is a miss. Receive the message "Failed to download repository information... check your internet connection." I have network access. 

```
W:GPG error: http://download.opensuse.org  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A7D1D38BEB6D886, 
W:Failed to fetch http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found , 
W:Failed to fetch http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found , 
W:Failed to fetch http://ppa.launchpad.net/upubuntu-com/gtk+3.6/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found , 
W:Failed to fetch http://ppa.launchpad.net/upubuntu-com/gtk+3.6/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found , 
E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Went to [http://keyserver.ubuntu.com/](http://keyserver.ubuntu.com/) and copy and pasted to file key provided from the PUBKEY above 0xPUBKEY to desktop
sudo apt-key add desktop/key
OK

Ran update again and the same err displays, restarted the system and same message pops up. No other keys are listed.

---

### Post by QDR06VV9 on 2016-05-24
Have you yet tried this
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEY_ID 5A7D1D38BEB6D886
```
And try again with the update command  ...post back any errors

---

### Post by QDR06VV9 on 2016-05-24
And i see this PPA
```
deb http://ppa.launchpad.net/myunity/ppa/ubuntu YOUR_UBUNTU_VERSION_HERE main 
deb-src http://ppa.launchpad.net/myunity/ppa/ubuntu YOUR_UBUNTU_VERSION_HERE main 

```
Are Not supported for trusty (14.04)
They will need to be removed.
>                          [h=1][SIZE=2]     MyUnity [/SIZE][/h]                                                                          
             
                                                       
                                                                   [h=3][SIZE=2]PPA description[/SIZE][/h]   
    === The Official MyUnity PPA ===
 This PPA contains backports for Ubuntu Stable Releases (11.04/Natty  and 11.10/Oneiric). If you are using Precise (the current development  release, which in time will become 12.04), please don't use this PPA:  MyUnity is already availble from Ubuntu Archive through Ubuntu Software  Center.

   
     
      


---

### Post by hawaii243 on 2016-05-24
```
COW@SUSE:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEY_ID 5A7D1D38BEB6D886
[sudo] password for cow: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.nibhZMAcAU --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/myunity-ppa.gpg --keyring /etc/apt/trusted.gpg.d/noobslab-themes.gpg --keyring /etc/apt/trusted.gpg.d/numix-ppa.gpg --keyring /etc/apt/trusted.gpg.d/teejee2008-ppa.gpg --keyring /etc/apt/trusted.gpg.d/tualatrix-ppa.gpg --keyring /etc/apt/trusted.gpg.d/upubuntu-com-gtk_3_6.gpg --keyserver keyserver.ubuntu.com --recv-keys KEY_ID 5A7D1D38BEB6D886
gpg: "KEY_ID" not a key ID: skipping
gpg: requesting key BEB6D886 from hkp server keyserver.ubuntu.com
gpg: key BEB6D886: "home:Horst3180 OBS Project <home:Horst3180@build.opensuse.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
COW@SUSE:~$
```

what is up with the forums?!  had an entire format and forums cleared it all out and now double-posting....!

---

### Post by hawaii243 on 2016-05-24
> **runrickus said:**
> And i see this PPA
```
deb http://ppa.launchpad.net/myunity/ppa/ubuntu YOUR_UBUNTU_VERSION_HERE main 
deb-src http://ppa.launchpad.net/myunity/ppa/ubuntu YOUR_UBUNTU_VERSION_HERE main 

```
Are Not supported for trusty (14.04)


They worked fine when I first installed the PPA a few months ago.


Also:
```
      Last edited by runrickus; 2 Minutes Ago at 07:16 PM. Reason: Please use Code tags 
```

I had but someone is obviously messing around with the backend code of the ubuntuforum webserver and I lost a ton of edits, formatting, code and snippets... and it's all gone. Not posting that again.

---

### Post by QDR06VV9 on 2016-05-24
That's Very Odd as they only support 11.04 thru 11.10 and there is nothing there that is not already included in stock Repos for Trusty 14.04.
As you can plainly see in my Screenshot

---

### Post by hawaii243 on 2016-05-24
Not sure what to say, but it was working. 

Removed 
> myunity/ppa/ubuntu/dists/trusty/main/binary
upubuntu-com/gtk+3.6/ubuntu/dists/trusty/main/binary

Working fine now, tho no "upgrade" option to 16 LTS

---

### Post by QDR06VV9 on 2016-05-24
That upgrade option will become available when 16.04 reaches 16.04.1 the first point release in a few months from now.
So are you now in a good state as far as the package manager is concerned?

---

### Post by hawaii243 on 2016-05-24
Please explain... I see 16.04 has been the main distro for some while on ubuntu.com/download/desktop, so... linearly it ought to be available as an upgrade option. Anyway, I'll just use terminal. Thanks for the PPA help.

---

### Post by QDR06VV9 on 2016-05-24
A device running Ubuntu 14.04 LTS will only tell you there is a new Ubuntu update after the first point release goes live. In Xenial&#8217;s case that&#8217;s July.
In short: you won&#8217;t be notified of an upgrade this week.

But you don&#8217;t have to wait until the system gets around to telling you. You can upgrade right now.

See this but if it is not broke why chance a new problem?
[http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-14-04-to-ubuntu-16-04-lts](http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-14-04-to-ubuntu-16-04-lts)
Now if you are satisfied could you please mark this as solved as to help others.
Regards

---

