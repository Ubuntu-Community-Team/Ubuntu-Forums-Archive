---
title: "ubuntu-release-upgrader 21.04.11"
date: 2021-04-23
forum: Installation &amp; Upgrades
---

### Post by bert.ram.aerts on 2021-04-23
[TABLE="class: table, width: 100%"]
[TR]
[TD]I upgraded to Ubuntu 21.04 last Sunday from version 20.10.[/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
[https://www.ubuntuupdates.org/package_logs?type=dists&vals=hirsute](https://www.ubuntuupdates.org/package_logs?type=dists&vals=hirsute)
 lists ubuntu-release-upgrader with new version 21.04.11 for 3 packages

[LIST]
[*]     [python3-distupgrade]("https://www.ubuntuupdates.org/package/core/hirsute/main/updates/python3-distupgrade") 
[*]     [ubuntu-release-upgrader-core]("https://www.ubuntuupdates.org/package/core/hirsute/main/updates/ubuntu-release-upgrader-core") 
[*]     [ubuntu-release-upgrader-gtk]("https://www.ubuntuupdates.org/package/core/hirsute/main/updates/ubuntu-release-upgrader-gtk") 
[/LIST]

I have version 21.04.10 for all three and don't get this update. 

(base) bert@Dell7577Linux:~$ apt list | grep ubuntu-release-upgrader 
ubuntu-release-upgrader-core/hirsute,hirsute,now 1:21.04.10 all [installed] 
ubuntu-release-upgrader-gtk/hirsute,hirsute,now 1:21.04.10 all [installed]   <--- 10 
ubuntu-release-upgrader-qt/hirsute-updates,hirsute-updates 1:21.04.11 all    <--- 11 
 
(base) bert@Dell7577Linux:~$ apt list | grep python3-distupgrade 
python3-distupgrade/hirsute,hirsute,now 1:21.04.10 all [installed]           <--- 10 

What is wrong?

---

### Post by grahammechanical on 2021-04-23
Packages listed as "proposed" do not get downloaded as a normal update/upgrade. We need to activate the Proposed repository. Software & Updates>developer Options. Do that on any version of Ubuntu - Released, newly released or development release and we risk things breaking. Having a proposed repository is a way of allowing users to test packages about to be downloaded into released versions of Ubuntu.

We like to think that on release day we get a new, finished version of Ubuntu but in truth development is still taking place. Updating regularly will still bring in updated packages for the next few days.

Regards

---

### Post by deadflowr on 2021-04-23
> What is wrong?


Nothing.
Ubuntu 21.04 uses phased-updates for all apt now.
(before it was used only for update-manager)


Oddly, you also have the qt version, though I'm not sure why.
(Even odder as it has been updated to the newest version)

---

### Post by bert.ram.aerts on 2021-04-23
to grahammechanical

Allowing proposed packages, doesn't change anything for the mentioned packages... These are really released as updates, but in fact not available.

---

### Post by bert.ram.aerts on 2021-04-23
to deadflowr

ubuntu-release-upgrader-qt is not installed, but is listed as the new version...

---

### Post by deadflowr on 2021-04-23
My point remains, it's phased updates.

---

### Post by bert.ram.aerts on 2021-04-23
@deadflowr

You are perfectly right.

After 
sudo mv /etc/machine-id /etc/machine-id.org
I indeed get
(base) bert@Dell7577Linux:~$ apt list --upgradable 
Listing... Done 
python3-distupgrade/hirsute-updates,hirsute-updates 1:21.04.11 all [upgradable from: 1:21.04.10] 
ubuntu-release-upgrader-core/hirsute-updates,hirsute-updates 1:21.04.11 all [upgradable from: 1:21.04.10] 
ubuntu-release-upgrader-gtk/hirsute-updates,hirsute-updates 1:21.04.11 all [upgradable from: 1:21.04.10] 

Not sure if I am going to allow these phased updates...

---

