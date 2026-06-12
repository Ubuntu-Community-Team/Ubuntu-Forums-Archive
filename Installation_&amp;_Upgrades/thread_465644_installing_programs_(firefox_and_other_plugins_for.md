---
title: "installing programs (firefox and other plugins for media player)"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by jasonaz on 2007-06-05
hey guys, im wondering how do u install firefox (the new version) and the other plugins required to play files on the installed media players in ubuntu...i cant seem to get it workin mainly coz it wont let me log as root...ive set a new password for root but on the logon screen when i try to log on root it wont let me..if i use sudo it just wont work at all...at the moment im logged on usin my other account..please help me guys

---

### Post by NeoLithium on 2007-06-05
I believe when you download the new firefox .tar.gz, you have to unpack it in /usr/lib  thereby it will overwrite your previous version with the newer one.

So you just download it, open up a terminal, CD to the directory where the .tar.gz saved and type each of the lines below (seperately)
  
```

(Make sure you switch the firefox.XXX to the actual name)

sudo mv firefox.XXX.tar.gz /usr/lib

cd /usr/lib

sudo tar -xvzf firefox.XXX.tar.gz

sudo rm firefox.XXX.tar.gz

```

Should work nicely.  As for the plugins, if you meant the media player stuff, check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org) It has a nice walkthrough for the codecs and plugins for firefox.

---

### Post by jasonaz on 2007-06-05
> **NeoLithium said:**
> I believe when you download the new firefox .tar.gz, you have to unpack it in /usr/lib  thereby it will overwrite your previous version with the newer one.

So you just download it, open up a terminal, CD to the directory where the .tar.gz saved and type each of the lines below (seperately)
  
```

(Make sure you switch the firefox.XXX to the actual name)

sudo mv firefox.XXX.tar.gz /usr/lib

cd /usr/lib

sudo tar -xvzf firefox.XXX.tar.gz

sudo rm firefox.XXX.tar.gz

```

Should work nicely.  As for the plugins, if you meant the media player stuff, check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org) It has a nice walkthrough for the codecs and plugins for firefox.
thanx but the deal is if i try to use the sudo command it will ask me for d root password and then nothing happens...im thinkin of reformatting the thing from scratch since im on a dual boot machine and then reconfigure all the passwords

---

### Post by Bluecircle on 2007-06-05
You must use sudo in the terminal to run as root. Do not try to log in as root from the main login manager.

sudo <command>
then type your password and press enter, **no letters or *** will be shown.**


To install the latest firefox:

```

sudo apt-get install firefox

```

for flash support:

```

sudo apt-get install flashplugin-nonfree

```

for java:

```

sudo apt-get install java-common

```

for win32 codecs:

```

sudo apt-get install w32codecs

```

For updates, go to "Software Sources" under System -> Administration -> Software Sources

Enter your "sudo" password and click the updates tab and check "Important Security Updates" and "Recommended Updates". Then check the box to check daily (or whenever).

Then go to "Update Manager" under System -> Administration -> Update Manager

Enter your "sudo" password (if it asks you again) and click check for updates, and install any new available software.

---

### Post by Bluecircle on 2007-06-05
> **jasonaz said:**
> thanx but the deal is if i try to use the sudo command it will ask me for d root password and then nothing happens...im thinkin of reformatting the thing from scratch since im on a dual boot machine and then reconfigure all the passwords

Don't be so quick to quit. Do you know your sudo password? Nothing should appear when you type it. What happens when you put in your password and press enter?

---

### Post by jasonaz on 2007-06-06
when i type in sudo and then password nothin happens......im on the restricted user account and i cant even see the stuff people in here have posted that's supposed to be located in the admin menu

---

