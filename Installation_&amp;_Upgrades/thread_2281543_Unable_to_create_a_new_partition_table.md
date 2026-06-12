---
title: "Unable to create a new partition table"
date: 2015-06-07
forum: Installation &amp; Upgrades
---

### Post by noahmcbadass on 2015-06-07
I have recently acquired a used laptop and have been attempting to install Ubuntu onto it; however, when I reach step 4 in the installation stage I am not given any options, and instead forcied directly to the "something else" section. In addition, I have no disk to partition, it would seem. I will be the first to admit I have no idea what I am doing. Please help.
[ATTACH=CONFIG]262479[/ATTACH]

---

### Post by Elizine on 2015-06-08
Hi,

Please refer to the installation guide of Ubuntu  -http://www.ubuntu.com/download/desktop/install-ubuntu-desktop

---

### Post by deadflowr on 2015-06-08
Go to the top icon in the left pane (the icon that looks like Ubuntu logo) and click it to open the Ubuntu menu.
Then type "Terminal" and press enter.
Now in the Terminal run this command
```
sudo parted -l
```
post the output here if you please.

---

### Post by noahmcbadass on 2015-06-08
> **deadflowr said:**
> Go to the top icon in the left pane (the icon that looks like Ubuntu logo) and click it to open the Ubuntu menu.
Then type "Terminal" and press enter.
Now in the Terminal run this command
```
sudo parted -l
```
post the output here if you please.

[ATTACH=CONFIG]262489[/ATTACH]

---

### Post by Bashing-om on 2015-06-08
noahmcbadass; Does not look good for the home team !

We can assume that the 31.X drive given the identifier 'sda' is in fact a USB thumb drive. As it is the only device seen we can "assume" that bios is not able to pass on to the operating system anything about the internal hard drive.

So, what does bios have about the internal hard drive ? Is it listed in the bios settings utility ?

No ? Then it is open the box up - might be tough - and check the connections that they are tight and clean these at both the drive end and at the controller.
maybe the controller port is 'bad' ? 
A bit of a hassle but if cleaning does not reveal the internal drive in bios, tear it open again and swap to a different controller port .

Worst case situation: The controller on the hard drive is non-functional and OR the hard drive it's self has failed.

Until bios accepts the hard drive, there is nothing
[INDENT][INDENT][INDENT]the operating system can do
[/INDENT][/INDENT][/INDENT]

---

### Post by noahmcbadass on 2015-06-08
Thank you all for the help! I've determined that the laptop's hard drive was shot and managed to fix the issue by replacing the hard drive. Thanks much.

---

### Post by Bashing-om on 2015-06-08
noahmcbadass; Good deal !

Pleased you have resolution.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

