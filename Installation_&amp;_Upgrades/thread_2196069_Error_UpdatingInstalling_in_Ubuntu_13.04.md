---
title: "Error Updating/Installing in Ubuntu 13.04"
date: 2013-12-27
forum: Installation &amp; Upgrades
---

### Post by f2010185 on 2013-12-27
[COLOR=#333333][FONT=UbuntuRegular]I was trying to install git in my ubuntu using application manager.and got a "Required installation of untrusted packages error".i followed a few forums and tried to run sudo apt-get updateand i got this error[/FONT][/COLOR]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                                                                                                
  Could not connect to 172.16.0.20:8080 (172.16.0.20), connection timed out
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring Release.gpg                                                                                            
  Could not connect to 172.16.0.20:8080 (172.16.0.20), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg                                                                      
  Could not connect to 172.16.0.20:8080 (172.16.0.20), connection timed out
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                     
  Could not connect to 172.16.0.20:8080 (172.16.0.20), connection timed out
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-updates Release.gpg                                                                     
  Unable to connect to 172.16.0.20:8080:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) raring-backports Release.gpg
  Unable to connect to 172.16.0.20:8080:
Reading package lists... Done
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/raring/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/raring/Release.gpg)  Could not connect to 172.16.0.20:8080 (172.16.0.20), connection timed out

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg)  Unable to connect to 172.16.0.20:8080:

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/raring-backports/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/raring-backports/Release.gpg)  Unable to connect to 172.16.0.20:8080:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/raring-security/Release.gpg)  Could not connect to 172.16.0.20:8080 (172.16.0.20), connection timed out

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/raring/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/raring/Release.gpg)  Could not connect to 172.16.0.20:8080 (172.16.0.20), connection timed out

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)  Could not connect to 172.16.0.20:8080 (172.16.0.20), connection timed out

W: Some index files failed to download. They have been ignored, or old ones used instead.
[COLOR=#333333][FONT=UbuntuRegular]i thought it was a problem with the network connection and tried pinging google.com and it was working perfectly.Can anyone please help me with this.i am new to ubuntu[/FONT][/COLOR]

---

### Post by tfrue on 2013-12-28
Type:
```
sudo service networking restart
```

Then try and run 'sudo apt-get update'

Also, try and restart your computer, unplug your router for about 10 seconds then plug it back it. 

Then we can go from there.

Thanks,
Chris

---

### Post by claracc on 2013-12-28
You can try to change the server from which you download the software in repositories.

You can go yo the sources software gui, and then in settings window in tab ubuntu software, select other server to download the software.

Perhaps the server you are using 172.16.0.20 is overloaded.

---

### Post by f2010185 on 2013-12-28
is it sudo service networking-manager restart? it dint work :( and i tried connected to the main server as claracc suggested but then apt-get is not even able to read the package list.So there is a problem with network itself but i am not sure how to address it.

---

### Post by Iowan on 2013-12-28
> **f2010185 said:**
> is it sudo service networking-manager restart? it dint work :(

 sudo service network-manager restart

---

### Post by f2010185 on 2013-12-28
yes sorry there was a typo..i tried it.

 sudo service network-manager restart
 and then sudo ifconfig eth0 up   and then sudo dhclient eth0

---

### Post by Bashing-om on 2013-12-28
f2010185; Hi !

Networking is not my sphere of expertise, but sounds like you are not even getting out of your house.

What results from terminal code:
```

ping -c 3 8.8.8.8

``` which tries to contact Google's server( ip 8.8.8.8), 3 times; the result is an advisement of the connection.

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by f2010185 on 2013-12-28
the ping gave me an expected result.it works.

I think the problem is that i am not able to connect to the software repository

---

### Post by Bashing-om on 2013-12-28
f2010185; OK,

Next let's see if Domain Name Server is functional:
```

ping -c 3 ubuntu.com

```
If all still good, then;
So next is to determine the state of the package management system:
Post the outputs of terminal codes: (again)
```

sudo apt-get update
sudo apt-get upgrade

```

Did you change your mirror site per advisement ?

[INDENT][INDENT]there is cause and effect
[/INDENT][/INDENT]

---

### Post by f2010185 on 2013-12-28
yeah everything went well.that's not the problem i guess...may be we have to change the repository ip in some dll(equivalent) files

---

### Post by Bashing-om on 2013-12-28
f2010185;

All good now to where you can mark this thread as solved ?

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

### Post by f2010185 on 2013-12-29
no it's not resolved.

---

### Post by Bashing-om on 2013-12-29
f2010185; Strange !

OK what results if you load the URL directly into your browser ?
```

http://in.archive.ubuntu.com/ubuntu/dists/raring/Release.gpg

```
You should get the "PGP SIGNATURE" ( I do when I test it ).
And maybe you no longer have a valid key on your system.
What returns from terminal command:
```

ls -la ~/.gnupg

```

[INDENT][INDENT]look'n for a reason
[/INDENT][/INDENT]

---

### Post by mörgæs on 2013-12-29
@f2010185 , 13.04 has only one month of support left. Wasn't it better to do a fresh install of 13.10 now?

---

