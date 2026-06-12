---
title: "Citrix ICA XenApp on 64 bit Lucid."
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by odinb on 2010-05-04
Anyone have any info on how to go about in this situation with a 64-bit version of Lucid, and XenApp?

Citrix only has 32-bit packages available on their web, and previously with Karmic, you just added some 32-bit libs, and it would work. But now the "GDebi Pack*ager Installer" refuses to do the install, since this is a 32-bit package, and throws you this error: "Error: Wrong architecture 'i386'"

Anyone out there that has managed to find a workaround to install this?

---

### Post by odinb on 2010-05-05
Fixed it using the force command!

Here is the guide if someone else runs into the same issue:

Install Citrix ICA XenApp Client in 64-bit Ubuntu 10.04

* First, go [www.citrix.com](www.citrix.com) to download the &#8220;Citrix XenApp&#8221; client. Make sure you get the Linux .deb package, it is only available in 32-bit. ([http://www.citrix.com/site/SS/downloads/index.asp](http://www.citrix.com/site/SS/downloads/index.asp))

* Then, go ahead and install some libraries:
	sudo apt-get install libxaw7 libmotif3 ia32-libs

* Then we need to force install the .deb package since the ICA XenApp is not available for 64-bit OS:
	sudo dpkg -i --force-all icaclient_11.100_i386.patched.deb

  Please note that the package name might change in the future.
  The package is now installed in /usr/lib/ICAClient/

* At first launch, Firefox will ask you what to do with the launch.ica file. Choose "Open with" and click the "Browse" button.
  Browse to /usr/lib/ICAClient/ and click the "wfica" binary.
  If you do not want to have to do this every time, tick the box that says "Do this automatically for files like this from now on.", then click "ok".

* Terminal server should now work.

---

### Post by SoeperFriek on 2010-05-06
You are the best!! I already gave up when I saw the error, but thanks to you I'm happily logged on at work! (can you imagine..? ;) )

/offtopic 
This is why I love Ubuntu and users like you! Even the Citrix-package is getting better now. (not there yet..) But U10.4 is amazing. Can even use my iPods.

Thanx-a-lot, you made my day. Almost installed Windows in a VM... no need for it now. :)

---

### Post by odinb on 2010-05-06
> **SoeperFriek said:**
> 
Thanx-a-lot, you made my day. Almost installed Windows in a VM... no need for it now. :)

Great!

Did that already in 2007 (Ubuntu 7.04). Run virtualbox for my Windows instances, and boot it more and more rarely! Now it is basically only if i need to re-program my remote (Harmony) or to lend a book (Adobe Digital Editions) at the virtual branch of the library and then to strip the DRM so it can be loaded onto the Nook.

Can recommend virtualbox! Hope the greedy Oracle does not start charging for it like they did the odf-plugin for MS-office!

-------------------------------------------------------------------------
Up to two hours of broadband to ftp the Linux package - 15 cents;
CD's to burn the files - $1.00;
The knowledge that nothing on your computer is from Microsoft - PRICELESS;
There are some operating systems that you don't need money to buy,
for everyone else... there's Windows&#8482;
©Instant Attitudes. All Rights Reserved.

---

### Post by yuesong on 2010-05-06
Hi,

I followed the steps but couldn't get it to work. Below is the error I get when I run the sudo dpkg command. Any help is greatly appreciated!

dpkg: warning: overriding problem because --force enabled:
package architecture (i386) does not match system (amd64)
(Reading database ... 145189 files and directories currently installed.)
Preparing to replace icaclient 11.100 (using icaclient_11.100_i386.patched.deb) ...
/var/lib/dpkg/info/icaclient.prerm: line 22: /usr/lib/ICAClient/util/echo_cmd: No such file or directory
Unpacking replacement icaclient ...
Setting up icaclient (11.100) ...
/var/lib/dpkg/info/icaclient.postinst: line 22: /usr/lib/ICAClient/util/echo_cmd: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 397: /usr/lib/ICAClient/util/echo_cmd: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 295: /pkginf/Ver.core.linuxx86: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 296: /pkginf/Ver.core.linuxx86: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 297: /pkginf/Ver.core.linuxx86: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 298: /pkginf/Ver.core.linuxx86: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 299: /pkginf/Ver.core.linuxx86: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 300: /pkginf/Ver.core.linuxx86: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 301: /pkginf/Ver.core.linuxx86: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 302: /pkginf/Ver.core.linuxx86: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 304: /pkginf/changeno.dat: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 310: /pkginf/Ver.core.linuxx86: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 312: /pkginf/Ver.core.linuxx86: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 313: /pkginf/Ver.core.linuxx86: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 316: /pkginf/F.core.linuxx86: No such file or directory
chmod: cannot access `/pkginf/Ver.core.linuxx86': No such file or directory
chmod: cannot access `/pkginf/F.core.linuxx86': No such file or directory
No target eula.txt found under . for en_US.UTF-8
chmod: cannot access `./nls/en/eula.txt': No such file or directory
No target Npica.ad found under . for en_US.UTF-8
chmod: cannot access `./nls/en/Npica.ad': No such file or directory
ln: creating symbolic link `Npica': File exists
/var/lib/dpkg/info/icaclient.postinst: line 2495: cd: config: No such file or directory
No target module.ini found under .. for en_US.UTF-8
chmod: cannot access `../nls/en/module.ini': No such file or directory
ln: creating symbolic link `/config/module.ini': No such file or directory
No target wfclient.ini found under .. for en_US.UTF-8
chmod: cannot access `../nls/en/wfclient.ini': No such file or directory
ln: creating symbolic link `/config/wfclient.ini': No such file or directory
No target appsrv.ini found under .. for en_US.UTF-8
chmod: cannot access `../nls/en/appsrv.ini': No such file or directory
ln: creating symbolic link `/config/appsrv.ini': No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 2522: cd: ../help: No such file or directory
No target index.htm found under .. for en_US.UTF-8
chmod: cannot access `../nls/en/index.htm': No such file or directory
ln: creating symbolic link `/help/index.htm': No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 397: /usr/lib/ICAClient/util/echo_cmd: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 700: /usr/local/lib/netscape/mailcap: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 706: /usr/local/lib/netscape/mime.types: No such file or directory
grep: /usr/local/lib/netscape/mime.types: No such file or directory
grep: /usr/local/lib/netscape/mailcap: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 973: /usr/lib/ICAClient/util/echo_cmd: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 974: /usr/lib/ICAClient/util/echo_cmd: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 973: /usr/lib/ICAClient/util/echo_cmd: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 974: /usr/lib/ICAClient/util/echo_cmd: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 766: /usr/local/lib/netscape/mailcap: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 767: /usr/local/lib/netscape/mime.types: No such file or directory
/var/lib/dpkg/info/icaclient.postinst: line 397: /usr/lib/ICAClient/util/echo_cmd: No such file or directory
ln: creating symbolic link `/usr/local/lib/netscape/plugins/npica.so': No such file or directory

It did create the /usr/lib/ICAClient directory and all the files but I can't seem to run any of the executables. For example, If I do

/usr/lib/ICAClient/wfica

I get

bash: /usr/lib/ICAClient/wfica: No such file or directory

I'm rather new to linux. The errors don't make much sense to me, especially because the files are there.

I really hope if you can give me a pointer.

Thanks a ton!

Yuesong

P.S. odinb, I sent you an email with the same question. Please ignore it that was before my registration to the forum came through. Sorry about that.

---

### Post by yuesong on 2010-05-07
Hey I got it to work! I had a fresh installation of Lucid, so something must have been missing when I installed citrix first time around. After I installed the Flash plugin for FF for something else I needed, I decided to look at the situation again, and happened to notice that wfica was giving me a different error message, which indicated that it could actually run. So I re-installed the package, and it works perfectly now. It's shame I can't tell exactly what was missing :( But thanks for the post just the same! It is much easier than what I had to do for 9.10!

---

### Post by ds77 on 2010-05-26
Thank you odinb!  I just stumbled upon your post after looking at a dozen or so others with no luck.  Works great in Chromium.  I still hate the way chrome has to download everything rather then just run it if you allow it, but at least it works.  Citrix actually works better in ubuntu then on a windows pc.

To Citrix- get on the ball and get a 64client out already! 32bit is old news :)

---

### Post by dacow on 2010-07-18
I just installed Ubuntu and I'm getting the same errors as Yuesong. I really don't want to reinstall it to get it to work :(

Any ideas? Sorry to dig up an old thread!

---- EDIT----

Incase anyone else has the same issue.. had to install ia32-libs..

sudo apt-get install ia32-libs

Then run the install for ICA and it works :)

---

### Post by timothydonohue on 2011-02-13
awesome guys, thanks for the helps

i followed the instructions in post 2, with some modifications...

i my icaclient didn't have the correct security certificate from digicert, so i had to do a manual install of that.  

i also had to create a link that went from the mozilla plugins folder to some .so file in icaclient folder (sorry i can't remember, i closed the tab already, easy enough to find solution via google though)

---

### Post by cabotcat on 2012-02-13
Have been trying to get this done for days on end. Followed the 64 bit instructions here:

[http://ubuntuforums.org/showthread.php?t=1837254&highlight=citrix](http://ubuntuforums.org/showthread.php?t=1837254&highlight=citrix)

I can logon and see my email icon and desktop icon but when I click either one I get a blank Firefox page. Not sure what I am doing wrong.

I am running 11.10 on a Dell Latitude 64 bit laptop. Any and all help greatly appreciated.

---

