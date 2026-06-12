---
title: "Install a .run package."
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by Animal0307 on 2010-05-25
I am trying to install a driver for my ATI AIW 9600. I have downloaded the driver from ATI's website and got a .run file. After some googling I found some steps here: [https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage). I made it all the way to the terminal, I get loading dots, and then a message window saying I need to run as a super user. How do I do this? Please be descriptive as I am new to Linux. Also sorry if this is in the wrong spot on the forum. I new here too.

---

### Post by spcwingo on 2010-05-25
sudo = Super User DO

Just put sudo in front of whatever command you're trying to run.  ;)

For example:

instead of:

```
file_name.run
```

use instead:

```
sudo file_name.run
```

---

### Post by Animal0307 on 2010-05-25
I put this in:
"sudo driver.run"
And this is what I got back:
"sudo: driver.run: command not found"

I have the file on my desktop and I renamed it "driver" because it was long an complicated before. Did I do something wrong or do I need to do something else because I have the file on my desktop?

---

### Post by spcwingo on 2010-05-25
If it's on your desktop and named driver.run, you would open a terminal and input these commands:

```
cd Desktop
```

then:

```
sudo ./driver.run
```

Now, the explanation of those commands:

cd Desktop = Change Directory to Desktop

sudo ./driver.run = sudo (Super User DO) ./ [(this directory)this is needed because Linux in general uses what's called a path] driver.run (no explanation needed)

More on paths here:

[http://www.linfo.org/path_env_var.html]("http://www.linfo.org/path_env_var.html")

---

### Post by Animal0307 on 2010-05-26
Thanks a lot for the help. I managed to get it installed, but it says its not working. Either I didn't install the right driver or it's not functioning properly. I don't think I installed the driver just ATI's catalyst controller thing. I starting to hate ATI. Got any tips?

---

### Post by spcwingo on 2010-05-26
Please post the output of this command ran from a terminal:

```
uname -a
```

Then we can proceed from there.

---

### Post by i.r.id10t on 2010-05-26
sudo sh run_this.run

---

### Post by Animal0307 on 2010-05-27
> **spcwingo said:**
> Please post the output of this command ran from a terminal:

```
uname -a
```Then we can proceed from there.
 

paul@paul-desktop:~$ uname -a
Linux paul-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

Thats what I got when i put in the code you gave me.

---

### Post by spcwingo on 2010-05-27
That's the output that I needed to determine the architecture of your system.  You can try a program called envyng.  You can download it here:

[http://launchpadlibrarian.net/31627938/envyng-core_2.0.1ubuntu3_all.deb]("http://launchpadlibrarian.net/31627938/envyng-core_2.0.1ubuntu3_all.deb")

To make this easier save it to your /home/username/ folder.  Now press CTRL+ALT+F1.  This should drop you to a terminal.  Login (you won't see any feedback when you type your password) and input this command:

```
sudo /etc/init.d/gdm stop
```

followed by your password.

After that run this command:

```
sudo dpkg -i ./envyng-core_2.0.1ubuntu3_all.deb
```

When it gets done installing that package run this command:

```
envyng -t
```

After that just follow the on-screen directions (they're pretty straightforward).  Hopefully after that you will have your ATI binary driver working (after the recommended reboot, of course).  Let me know how it turns out.

---

### Post by jocko on 2010-05-28
> **Animal0307 said:**
> I am trying to install a driver for my ATI AIW [COLOR=Red]9600[/COLOR]. I have downloaded the driver from [COLOR=Red]ATI's website[/COLOR] and got a .run file.
ATi does NOT make any driver for that card anymore. They abandoned support for it (along with all other cards older than the radeon HD series) more than one year ago.
And the old catalyst 9.3 driver which was the last driver to support your card will NOT work on any ubuntu release newer than 8.10.

The open source driver (radeon), which installed by default in ubuntu is the only driver you can use.

---

### Post by Animal0307 on 2010-05-30
Ok I've got the file downloaded. It tried to open in with something called Package Installer. I canceled it and tried to run like you said. I have the file sitting in my home folder but when I hit Ctr + Alt + F1 my screen went black, monitor went to sleep, and I couldn't do anything, I wasn't sure if this was suppose to happen so I let it sit for 10 - 15 minutes and nothing. So I reset and tried again. But the same thing happened. Any ideas?

---

### Post by spcwingo on 2010-05-30
Okay, let's try it this way:

Open a terminal and type:

```
envyng -t
```

Then follow the instructions.  At the end it will ask if you want to reboot...reply with yes.  Let me know if that gets the job done.

---

### Post by jocko on 2010-05-30
Did you not [read my post]("http://ubuntuforums.org/showpost.php?p=9371823&postcount=10")?

There is **no other driver for your card than the one that is already installed and active by default.** Any attempt to install ati's proprietary driver (fglrx) will only result in a broken xorg.
envyng will NOT change this. It will only install a driver which does NOT support your card.

---

### Post by Animal0307 on 2010-05-30
> **jocko said:**
> Did you not [read my post]("http://ubuntuforums.org/showpost.php?p=9371823&postcount=10")?

There is **no other driver for your card than the one that is already installed and active by default.** Any attempt to install ati's proprietary driver (fglrx) will only result in a broken xorg.
envyng will NOT change this. It will only install a driver which does NOT support your card.

No I did not see your post early. But thank you for the explanation.

---

