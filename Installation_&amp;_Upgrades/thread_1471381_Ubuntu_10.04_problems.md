---
title: "Ubuntu 10.04 problems"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Jan Greeff on 2010-05-03
Since upgrading to Ubuntu 10.04, my Open Office documents take ages to open. Also, the system does not open pdf documents. Both these problems arose immediately after the upgrade. How do I go about sorting these bugs out, please?

---

### Post by Ad@m on 2010-05-03
A lot of people are experiencing issues when they upgrade.

My only suggestion is to do a clean install.

---

### Post by tgalati4 on 2010-05-03
Open a terminal:

cd
cd Documents
evince anypdfthatwontopen.pdf

Post the output of any errors.

---

### Post by Jan Greeff on 2010-05-05
> **tgalati4 said:**
> Open a terminal:

cd
cd Documents
evince anypdfthatwontopen.pdf

Post the output of any errors.

Thanks, the pdf docs problem was solved by installing Acrobat (this program was removed by the upgrade) but the opening of my Open Office documents remains - it takes a full 20 seconds for the system to open a document, which was done within 3 seconds by the old Ubuntu 9.10. This is frustrating.

---

### Post by tgalati4 on 2010-05-05
Can't help you with Open Office.  I don't have Lucid on any of my systems yet.  After the first OO document is open, subsequent documents should open quickly.  If each document takes 20 seconds (with OO already open) then you have a real problem.

On my Intrepid machine (dual core, 3 GHz) it takes OO about 3 seconds to open the first document and 1-2 seconds for each subsequent document.

Find a stopwatch and try in a terminal:

cd
cd Documents
oowriter --debug  mydocument.odt

Take note of the time to open the first document, then do file-->open recent and bring up a few other docs and time how long they take to come up.

Post any errors in the terminal window.

---

### Post by Jan Greeff on 2010-05-05
Terminal result was that there is no "My document" file. I tried "My documents" and got the same result.

---

### Post by tgalati4 on 2010-05-06
You were suppossed to use one of your files.  mydocument.odt was a placeholder.

---

### Post by Jan Greeff on 2010-05-11
> **tgalati4 said:**
> You were suppossed to use one of your files.  mydocument.odt was a placeholder.
I have tried a number of times, the feedback from the terminal is always that the document does not exist. 

Some of the oft-used documents start opening quicker, but only until the computer is restarted, then back to 20 seconds for them all.

---

### Post by Tombgeek on 2010-06-08
Hey,

I am also experiencing the same issues. I recently upgraded to Ubuntu 10.04 and I have been having the same issues with OpenOffice.
It does take a while to open up a document, whether I double click on the document or use File -> Open.
It still takes about 20 - 25 seconds to load.

As an aspiring writer, it not not every encouraging to have a word processor that takes forever to open files. I am currently using Abiword, only until the issues with OpenOffice Writer are fixed.

I installed the recent updates as well for OpenOffice, but so far, the problem has not been fixed.

---

### Post by Hagar Delest on 2010-06-09
First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, install the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Have you upgraded by soft upgrade or by a clean install with the live-CD? Avoid the former and prefer the latter. But it means that you've made several partitions before to keep your documents in a safe place of the HD, not impacted by the upgrade.

---

### Post by z06steve on 2010-06-09
I have the same problem on my laptop using 10.04 64-bit.  The initial opening of a document takes about 15-20 seconds with the screen going dark and then light once it opens.  I have a second computer with 10.04 64-bit install and it does not exhibit the problem.  I tried uninstalling and re-installing OpenOffice with no effect.....think I will download and try 3.2.1 tonight

---

### Post by z06steve on 2010-06-09
removed the default 3.2.0 install, downloaded 3.2.1 and installed it, I can now open documents in a second or two, not the 20-25 seconds it was taking before :-)

---

### Post by Tombgeek on 2010-06-10
> **Hagar de l'Est said:**
> First try to [reset your OOo user profile]("http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403") but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, install the Sun version: [[Ubuntu] Installing OOo on Debian and Co.]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68")

Have you upgraded by soft upgrade or by a clean install with the live-CD? Avoid the former and prefer the latter. But it means that you've made several partitions before to keep your documents in a safe place of the HD, not impacted by the upgrade.

> **z06steve said:**
> removed the default 3.2.0 install, downloaded 3.2.1 and installed it, I can now open documents in a second or two, not the 20-25 seconds it was taking before :-)

I did a clean install with a Live DVD.

Can I remove OpenOffice.org 3.2.0 through the software centre or do I have to do it through Synaptic?

---

### Post by Hagar Delest on 2010-06-10
Remove it from Synaptic. I've seen topics from users having tried from the software center and it seems that it doesn't remove all the packages in fact.

---

### Post by rcadby on 2010-06-10
I thought I fixed all my problems by installing 10.4 from the 'live' disc. The full install was done to a new partition, but I don't know how to get all the 'old' (home?) data & programs to work now. I don't see how to browse to the old partition.

For example, I no longer have my Thunderbird email, my FF bookmarks, my Evolution email or any of the other multitude of programs I used to have.

Can I get to the old partition and copy from there to the new one?

Sorry to be this stupid.

......Ron

PS: I've also lost the automatic connection to my router wireless. Doing this now with a cable. I forgot how I set up the wireless. It was years ago. Any easy guides?

---

### Post by Tombgeek on 2010-06-10
> **Hagar de l'Est said:**
> Remove it from Synaptic. I've seen topics from users having tried from the software center and it seems that it doesn't remove all the packages in fact.

Sorry to ask this, I am a bit of an idiot. I am still new to Ubuntu, so I am a bit scared of doing something that could potentially go wrong. In Synaptic, must I just search "openoffice" and mark everything that has a green check box?
Or can I just use 'sudo apt-get remove openoffice*' like someone else recommended on another thread?
I just downloaded OpenOffice.org 3.2.1

---

### Post by Hagar Delest on 2010-06-10
I think you can go the sudo apt-get remove way. Never tried it but it should work. And if it doesn't, just finish with Synaptic.

---

### Post by Tombgeek on 2010-06-10
> **Hagar de l'Est said:**
> I think you can go the sudo apt-get remove way. Never tried it but it should work. And if it doesn't, just finish with Synaptic.

Okay, it worked and I removed OpenOffice.org 3.2.0

Now, hehe :redface:, sorry to have to ask this. How the hell do I install it when I downloaded it from the site itself. I unziped the file to my desktop, which is called "OOO320_m18_native_packed-1_en-GB.9502", and it has three files inside, DEBS, licences and readmes, and a shell script called update.
I go into debs and there are 49 deb files, and I try to install all of them but some refuse to install, giving me a "Error: Dependency is not satisfiable: ooobasis3.2-en-GB"
Which I do not understand the problem because I did install a deb with a similar name.
Please help me out.
Sorry, I know I am a noob.

---

### Post by rcadby on 2010-06-10
> **rcadby said:**
> I thought I fixed all my problems by installing 10.4 from the 'live' disc. The full install was done to a new partition, but I don't know how to get all the 'old' (home?) data & programs to work now. I don't see how to browse to the old partition.

For example, I no longer have my Thunderbird email, my FF bookmarks, my Evolution email or any of the other multitude of programs I used to have.

Can I get to the old partition and copy from there to the new one?

Sorry to be this stupid.

**OK. I found the files. Looks like I have to install each application again. Oh, well. "You can't have everything. Where would you put it?" (George Carlin)**

......Ron

PS: I've also lost the automatic connection to my router wireless. Doing this now with a cable. I forgot how I set up the wireless. It was years ago. Any easy guides?

**However, I still need to find a guide for setting up my wireless again. Suggestions are welcome.**

---

### Post by Hagar Delest on 2010-06-10
> **Tombgeek said:**
> I go into debs and there are 49 deb files, and I try to install all of them but some refuse to install, giving me a "Error: Dependency is not satisfiable: ooobasis3.2-en-GB"
See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Tombgeek on 2010-06-11
> christopher@christopher-desktop:~$ cd OOo320_m18_native_packed-1_en-GB.9502/DEB
bash: cd: OOo320_m18_native_packed-1_en-GB.9502/DEB: No such file or directory
christopher@christopher-desktop:~$ sudo dpkg -i *.deb
[sudo] password for christopher: 
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb


Okay, now what? The terminal gives me an error

---

### Post by Hagar Delest on 2010-06-11
> **Tombgeek said:**
> Okay, now what? The terminal gives me an error
Have you downloaded the GB version? If so it won't work because the file name is different. That's why I don't like tutorials where the full file name is given, it can mislead users. See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) and have a look at the tab autocompletion trick.

---

### Post by z06steve on 2010-06-11
It took me awhile of searching om their site to finally find this.....

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=68)

1. Remove all the packages from the installed version
Go to Synaptic or your package manager and mark all the openoffice.org packages installed to be removed (there is the string ubuntu in their version number). This is mandatory for your first upgrade of the distro delivered OOo version, no need to do that for the following upgrades.
Note: don't use the Ubuntu Software Center to remove OOo because it seems that some packages are left and conflict with the install with official debs.
For Ubuntu (flavors prior to Jaunty 9.04), the system will also remove the ubuntu-desktop package. No worry, this is a meta package that can be removed safely. But in case you want to upgrade your whole distro, you'll have to install back this package (and the OOo original version).

2. Download the tarball (.tar.gz file) from the official OOo web site
See here : [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html). Select the Linux DEB version!
If you've troubles getting the automatic download, see on the mirrors: [http://distribution.openoffice.org/mirrors/#mirrors](http://distribution.openoffice.org/mirrors/#mirrors).

3. Extract the tarball in your home directory (or any other directory you want)
Either do that with your file browser and your archive manager (usually available in the context menu) or open a terminal (you should be directly in your home directory) and :
CODE: SELECT ALL   EXPAND VIEW
tar -vxzf filename
Example (for 2.4.0): filename = OOo_2.4.0_LinuxIntel_install_en-US_deb.tar.gz
Hint: no need to type the whole filename, just start with the first characters and hit the TAB key for the auto-completion.

You should see a new folder, say OOo_inst_folder.
Example (for 2.4.0): OOo_inst_folder = OOH680_m12_native_packed-1_en-US.9286

4. Install the created .debs
CODE: SELECT ALL   COLLAPSE VIEW
cd OOo_inst_folder/DEBS
sudo dpkg -i *.deb

5. Update the Applications menu
Go to the desktop integration subfolder.
CODE: SELECT ALL   EXPAND VIEW
cd desktop-integration

Run again the previous installation command.
CODE: SELECT ALL   EXPAND VIEW
sudo dpkg -i *.deb

---

### Post by Hagar Delest on 2010-06-11
No need to quote the message, that's precisely the link I've given above!

---

