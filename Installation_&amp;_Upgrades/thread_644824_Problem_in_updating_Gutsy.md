---
title: "Problem in updating Gutsy"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by Zdravko on 2007-12-19
I just installed Gutsy and I have a problem with the updates.

Also, Firefox was unable to install the adobe flash plugin. Only GNASH "almost" succeeded, but I doubt the flash sites open properly.


Can you help me investigating the errors I get?

---

### Post by Zdravko on 2007-12-19
Anyone?

---

### Post by chewearn on 2007-12-19
> **Zdravko said:**
> I just installed Gutsy and I have a problem with the updates.
What error messages are you getting?

> Also, Firefox was unable to install the adobe flash plugin. Only GNASH "almost" succeeded, but I doubt the flash sites open properly.
Did you install flash via "Add/Remove..." menu?  What error messages are you getting?

> Can you help me investigating the errors I get?

What error messages are you getting? :)

---

### Post by Nano Geek on 2007-12-19
First off, don't bump a thread after only 40 minutes.

And second, you need to be more specific than just telling us that you have problems. To install the Flash plugin, did you get it from Ubuntu's repository and if so, what error did it give you?

---

### Post by Zdravko on 2007-12-19
I started Firefox and opened a web site. A yellow bar appeared at the top offering me to install Adobe or GNASH flash player.  The Adobe one installed with errors. After restarting Firefox the web site again triggered the yellow bar. This time I chose the GNASH. Again - a lot of errors during install. After restart of Firefox - the web site loads without yellow bar, but the flash images seem corrupt.
How do I show you the errors?

---

### Post by chewearn on 2007-12-19
> **Zdravko said:**
> I started Firefox and opened a web site. A yellow bar appeared at the top offering me to install Adobe or GNASH flash player.  The Adobe one installed with errors. After restarting Firefox the web site again triggered the yellow bar. This time I chose the GNASH. Again - a lot of errors during install. After restart of Firefox - the web site loads without yellow bar, but the flash images seem corrupt.
How do I show you the errors?

Try this:
Use synaptic, search for "flash".  Remove gnash, and install flashplugin-nonfree package.

---

### Post by Zdravko on 2007-12-19
I tried to remove completely gnash and the adobe one (or whatever its name is). Then I installed flashplugin-nonfree. Or at least tried to do so. But the black box issued a md5 mismatch. The plugin is NOT installed.

---

### Post by Nano Geek on 2007-12-19
This should fix your problem. ```
sudo apt-get remove gnash && sudo apt-get install flashplugin-nonfree
```

---

### Post by Zdravko on 2007-12-19
Is it ok:
> zdravko@ubuntu:~$ sudo apt-get remove gnash && sudo apt-get install flashplugin-nonfree
[sudo] password for zdravko:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by Zdravko on 2007-12-19
Nope. It isn't ok. The website still doesn't show animations :cry:

---

### Post by Zdravko on 2007-12-19
And the yellow bar appears again, after restarting firefox... This looks like an evil endless cycle...

---

### Post by Nano Geek on 2007-12-19
What website are you trying to look at?

---

### Post by Zdravko on 2007-12-19
[http://forums.bgdev.org/](http://forums.bgdev.org/)

---

### Post by Nano Geek on 2007-12-19
I don't see any flash on that page.
Can you direct me to the specific page that had the flash content on it?

---

### Post by Zdravko on 2007-12-19
I also don't see flash. Because the plugin is not working. Maybe your plugin also does not work.
Here is another site that pop ups a yellow bar: [http://www.jarcomputers.com/](http://www.jarcomputers.com/)

---

### Post by lswest on 2007-12-19
the problem with flash has been addressed many many times before, the problem is adobe updated a driver, and the repos still carry the old md5 sum, so you're going to have to go to [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux") and download the tar.gz and after extracting it double-click on the script, and choose "run in terminal" then follow the instructions and keep in mind that the path for firefox is /usr/lib/firefox/  as for the gutsy problems, i need more information too.

---

### Post by Nano Geek on 2007-12-19
Again, no flash, no yellow bar.
Does Youtube work for you?

---

### Post by Zdravko on 2007-12-19
> **lswest said:**
> the problem with flash has been addressed many many times before, the problem is adobe updated a driver, and the repos still carry the old md5 sum, so you're going to have to go to [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux") and download the tar.gz and after extracting it double-click on the script, and choose "run in terminal" then follow the instructions and keep in mind that the path for firefox is /usr/lib/firefox/  as for the gutsy problems, i need more information too.
What kind of instructions? Nothing happens after Run in terminal...

---

### Post by Zdravko on 2007-12-19
> **asjdfwejqrfjcvm msz34rq33 said:**
> Again, no flash, no yellow bar.
Does Youtube work for you?

Nope, yellow bar.

---

### Post by chewearn on 2007-12-19
> **Zdravko said:**
> [http://forums.bgdev.org/](http://forums.bgdev.org/)

There is a flash element in the page, which points to:
[http://www.bgdev.org/uploads/banners/ComputerSpace2007.swf](http://www.bgdev.org/uploads/banners/ComputerSpace2007.swf)

I have NoScript plugin, which tells me the element is there, but if I temporary allow it to load, it doesn't display anything.

---

### Post by Zdravko on 2007-12-19
[AstalaVista]("http://ubuntuforums.org/member.php?u=234265"),... which means you have the same problem as I.

---

### Post by chewearn on 2007-12-19
Ok, just a wild guess here, are you running 64-bit ubuntu?

If you did run 64-bit ubuntu, then you need to install a second 32-bit Firefox.  There is a script to help you do this in the x86_64 forum.

When I open the page in 32-bit firefox, I still get a "blank" flash for the page [http://forums.bgdev.org/](http://forums.bgdev.org/), but youtube works.

---

### Post by Zdravko on 2007-12-19
Yes, I run a 64 bit Ubuntu. What is the problem?

---

### Post by chewearn on 2007-12-19
I have to install a second 32-bit Firefox to get java and flash running properly.  Currently, there is no 64-bit sun java, and I'm not sure what's wrong with the 64-bit adobe flash.

---

### Post by Nano Geek on 2007-12-19
Zdravko, can you tell us if Youtube works on your computer?

---

### Post by buntu_hugenewbie11 on 2007-12-19
I had the same problem.
See here for a solution: [http://ubuntuforums.org/showthread.php?p=3961576#post3961576](http://ubuntuforums.org/showthread.php?p=3961576#post3961576)
and here are the scripts you need:
[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)
Tell Cyrus thanks.

---

### Post by lswest on 2007-12-19
about the flash player install script, sorry my bad got it confused with my fontinstall.sh.  You need to run the script as root, so do ```
 sudo sh ./[name of file].sh
``` in the folder where the script is.  should work then

---

### Post by Zdravko on 2007-12-20
> **asjdfwejqrfjcvm msz34rq33 said:**
> Zdravko, can you tell us if Youtube works on your computer?
I told you! In order to play something the yellow bar appears!

---

### Post by chewearn on 2007-12-20
hi Zdravko
Here is the link to install a 32-bit Firefox on the 64-bit ubuntu:
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

### Post by Zdravko on 2007-12-20
Why would I install a 32 bit Firefox? That is weird.
I followed these instructions:
>  1. sudo apt-get install flashplugin-nonfree
2. sudo nano /var/lib/dpkg/info/flashplugin-nonfree.postinst
3. Edit:
 	Code:
 	# verify MD5 checksum of (copied or downloaded) tarball
rm -rf install_flash_player_9_linux/
echo "821cc72359a937caef85bb4cc74ef5cd install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

# unpacking and checking the plugin
tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
echo "be5a2f9032f8fc8bccbbf5d96c5028f9 install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted"
echo "a81fd3b03b8c6d6e5a14298110718d3f install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/null 2>&1 \
|| fp_exit_with_error "plugin changed, not trusted" 
to:
 	Code:
 	        # verify MD5 checksum of (copied or downloaded) tarball
        rm -rf install_flash_player_9_linux/
        echo "93b7c48eaa492237b807a3ae1de65cf9  install_flash_player_9_linux.tar.gz"| md5sum -c > /dev/null 2>&1 \
                || fp_exit_with_error "md5sum mismatch install_flash_player_9_linux.tar.gz"

        # unpacking and checking the plugin
        tar xzf install_flash_player_9_linux.tar.gz || fp_exit_with_error "cannot unpack plugin"
        #echo "a81fd3b03b8c6d6e5a14298110718d3f  install_flash_player_9_linux/flashplayer.xpt"| md5sum -c > /dev/$
        #echo "13ce705df5d47422a9192b29827544e8  install_flash_player_9_linux/libflashplayer.so"| md5sum -c > /de$
        #       || fp_exit_with_error "plugin changed, not trusted" 
4. sudo dpkg-reconfigure flashplugin-nonfree
5. nspluginwrapper -v -a -i


I got:
> zdravko@ubuntu:~$ nspluginwrapper -v -a -i
Auto-install plugins from /usr/lib/mozilla/plugins
Looking for plugins in /usr/lib/mozilla/plugins
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libtotem-basic-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64
Auto-install plugins from /usr/lib64/mozilla/plugins
Looking for plugins in /usr/lib64/mozilla/plugins
*** NSPlugin Viewer  *** ERROR: /usr/lib64/mozilla/plugins/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib64/mozilla/plugins/libtotem-basic-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib64/mozilla/plugins/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib64/mozilla/plugins/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64
Auto-install plugins from /usr/lib/firefox/plugins
Looking for plugins in /usr/lib/firefox/plugins
*** NSPlugin Viewer  *** ERROR: /usr/lib/firefox/plugins/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/firefox/plugins/libtotem-basic-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/firefox/plugins/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib/firefox/plugins/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64
Auto-install plugins from /usr/lib64/firefox/plugins
Looking for plugins in /usr/lib64/firefox/plugins
*** NSPlugin Viewer  *** ERROR: /usr/lib64/firefox/plugins/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib64/firefox/plugins/libtotem-basic-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib64/firefox/plugins/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64
*** NSPlugin Viewer  *** ERROR: /usr/lib64/firefox/plugins/libtotem-narrowspace-plugin.so: wrong ELF class: ELFCLASS64
Auto-install plugins from /home/zdravko/.mozilla/plugins
Looking for plugins in /home/zdravko/.mozilla/plugins


But at the end I have flash! :)

---

### Post by chewearn on 2007-12-20
> **Zdravko said:**
> Why would I install a 32 bit Firefox? That is weird.

Now, it looks like adobe-flash 64-bit is working, but with (I believe) a md5sum problem; I don't understand all these technical issues, I just accept it.  But sun-java 64-bit firefox plug-in is not available.  Maybe you don't need java, that's fine.  But, later you might need it.  The best solution I can find is install 32-bit Firefox.  Then, every works as it should.

If I am just surfing the "plain" internet (that is, without the bells and whistles of java and flash), then I use the 64-bit Firefox, which I find to be faster.  But if I wanted to have flash, or java (for accessing banking sites), I switched to 32-bit Firefox.

It's probably a hassle to do this way.  Unfortunately, it's the most workable solution I can find right now.


> But at the end I have flash! :)

Congrats! :)

---

