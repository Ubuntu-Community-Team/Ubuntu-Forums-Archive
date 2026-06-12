---
title: "problem in installing ibm IBM Softcopy Reader in ubuntu 9.10"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by arunmanoj on 2009-12-19
hi!
 we are running a small training & consultancy company with around 35 pc,we are planning to move our entire network from windows xp to ubuntu 9.10(iam really new to linux),as we are giving ibm mainframe training,we have install ***[COLOR="Red"]"IBM Softcopy Reader" [/COLOR]*** in all pc's,i have downloaded 

***1) IBM Softcopy Reader from ***

[http://www-01.ibm.com/support/docview.wss?doc=4000251&org=SW&rs=4](http://www-01.ibm.com/support/docview.wss?doc=4000251&org=SW&rs=4)

***2) installation manual from ***

[ftp://ps.software.ibm.com/ps/products/bookmanager/tools/slinread.txt](ftp://ps.software.ibm.com/ps/products/bookmanager/tools/slinread.txt)

i can able to perform everything upto step 8,in step 9 i can't able to understand as there is no ***"/usr/share/gnome/apps"*** folder in ubuntu 9.10...pls help ***[COLOR="Red"]ASAP[/COLOR]***:confused::confused:

===================installation manual================================

[I]Download and Install From the IBM BookManager Web Site:
-----------------------------------------------------------

[COLOR="SeaGreen"]1. Start the Linux system.
2. Open your Web browser and go to IBM BookManager Web site: 
   [http://www.ibm.com/software/applications/office/bkmgr/softcopyread.html](http://www.ibm.com/software/applications/office/bkmgr/softcopyread.html)
3. Click on "Softcopy Reader for Linux" link.
4. Click on "Softcopy Reader for Linux V3.7" link.
   A dialog will prompt for a save location.
5. Select a suitable place download the .tgz file.
   The Softcopy Reader file will be downloaded to this location.
6. Open a terminal console window.  

Run the following steps in the terminal console:

7. "mkdir installdirectory"
   (replace installdirectory with the directory where the SCR program 
    is to reside.) 
8. "cd installdirectory" 
9.  "tar -zxvpf place_downloaded_to/ilrjaval.tgz"
   (replace place_downloaded_to with the directory where the .tgz file 
    was downloaded).

Scripts to run the Shelf Organizer and Book Reader are in
"installdirectory/sys".  These scripts are hlcs.sh and hlcb.sh.  
Add this directory to the user path as desired.  

There is limited support for file association under Linux.  To
do file association, first locate the hlcb.sh.desktop and 
hlcs.sh.desktop files in the install directory.  Next, change
the path specified under the lines starting with "Exec=" and 
"Icon=" to the path specified when untarring the Softcopy Reader 
package.  Note: if the Softcopy Reader package is untarred to
"/opt/scr", this step is not necessary.[/COLOR]

[COLOR="Red"]Next, copy both files to one of the following directories
depending on who will be using Softcopy Reader: 
  
Directory                  User 
---------                  -------------
/usr/share/applnk-redhat   All KDE users  
/usr/share/gnome/apps      All Gnome users
/etc/X11/applnk            All users
~/.kde/share/applnk-redhat Current user's when KDE is running
~/.gnome/apps              Current user when Gnome is running

Optionally you can copy the modified hlcb.sh.desktop and 
hlcs.sh.desktop files to your desktop, for example:
  For Fedura:
  copy the two files to ~/Desktop
  For Red Hat:
  copy the two files to ~/.gnome-desktop

Note: Before attempting to run SCR check that you have a setting for
      the environment variable LD_LIBRARY_PATH. This can be done via the 
      command "set" which will show all your Linux session parameters.
      Alternatively you can type "echo $LD_LIBRARY_PATH" to see 
      just that particular parameter.
      If LD_LIBRARY_PATH is not set, set it as follows:
      export LD_LIBRARY_PATH=/opt/scr/sys - ie set it to the sys directory
      where you installed SCR.

10.When installation is complete, you can start using Book
   Reader and Shelf Organizer. It is not necessary to 
   reboot your system.[/COLOR]
 
[/I]
===========================================================

,if i click the hlcb.sh..its not running...


THANX IN ADVANCE....

---

### Post by kev009 on 2009-12-21
Without any error messages to look at, I have a feeling that Java is not installed (which BookManager requires).

I am not a Ubuntu user so hopefully someone else can guide you through installing a JRE.

---

### Post by arunmanoj on 2009-12-21
JRE is installed & path is set...i can't able to understand the above text which are in red colour,as i can't able to find ***/usr/share/gnome/apps*** folder in ubuntu...:confused:

---

### Post by flint_ on 2012-02-17
Greetings,

I had problems with the IBM Softcopy reader, and I eventually fixed them.

The correct files are at:

[http://docbox.flint.com/~flint/ibm-softcopy-bookreader/](http://docbox.flint.com/~flint/ibm-softcopy-bookreader/)

Nothing fancy, but they work.

Cheers,

Flint

---

### Post by oldos2er on 2012-02-17
Closed, necromancy.

---

