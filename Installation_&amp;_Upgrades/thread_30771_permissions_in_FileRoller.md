---
title: "permissions in FileRoller"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by pdc on 2005-04-30
I have downloaded PageStream5 as a DTP programme;
I have copied it to /opt
the instructions are that one extracts it, and implements the "Run PageStream5" file;
by using FileRoller, I extract the component files as read-only; I select "All file" and glibly click on "Extract" and am told I do not have permission: I cannot see how I can claim "root" privileges from within FileRoller: (I somehow assume that is what I should do;)
I was not sure how to extract a .tar.bz2 file: the instructions from the Linux mag were to type "tar xvf --bzip2 <<filename>>.tar.bz2" and that elicited no file comment from the terminal ....

grateful for advice on gaining permission from within FileRoller to install this programme;

(.......needed to install a library lcms-1.14.tar.gz and that seems to have gone well .......)

---

### Post by jobezone on 2005-04-30
This is done with sudo or gksudo(graphical sudo).

Either do it in the Console:
"sudo file-roler"
Then enter you user password.

Or going to the menu Applications->Run Application:
"gksudo file-roler"
And enter your user password.

Also, the command that works for me is:
tar --bzip2 -xvf <<filename>>.tar.bz2

---

### Post by pdc on 2005-04-30
thank you very much for this most helpful advice:

I used the terminal; and your tar command advice worked perfectly; and PageStream extracted itself effortlessly; there is a file "Run PageStream5" and by typing ./Run PageStream5 it loads the programme;

so that is great;

**I would be grateful for one further piece of advice:** 
I thought to create a "Launcher" for the Panel: I entered the name PageStream; found the .png icon for it in the /opt drawer; and where the Launcher asks for a command, I clicked on the file "Run PageStream5", (that is in the /opt drawer;)

when I single-click on the icon in the panel, it baulks on the command:

it says:

Details: Failed to execute child process "/op/Run" (No such file or directory);

I could just open a terminal each time, but maybe nice to get the launcher working?

---

### Post by jobezone on 2005-04-30
"Details: Failed to execute child process "/op/Run" (No such file or directory);"

This is /opt/Run right?

Use this instead

"/opt/Run PageStream5"

as the command in your launcher. Because the file has a space in the middle of it, the launcher was trying to execute a file called just "Run" which it couldn't find in /opt . Puting it all under "" will work.

---

### Post by pdc on 2005-05-01
Bingo! All solved!

thanks very much for this: PageStream now loads beautifully from the icon launcher on the panel;

many thanks.

---

