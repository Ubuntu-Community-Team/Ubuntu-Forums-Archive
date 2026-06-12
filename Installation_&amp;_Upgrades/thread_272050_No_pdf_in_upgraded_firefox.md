---
title: "No pdf in upgraded firefox"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by jdpicka on 2006-10-05
Recently, I upgraded Firefox to 1.5.0.7.

Today, I noticed that pdf files did not display. Instead of Acroread firing up, I saw blanks whitness where the Acroread frame ought to have been. 

I followed the instructions on the wiki for fixing this. Nothing.
I installed Drake, and followed its instructions for fixing this. Nothing.
The comments that apt-get makes suggest that everything is where it ought to be, but still Firefox refuses to display any pdf documents.

Any ideas would be appreciated.

---

### Post by rcjhawk on 2006-11-09
> **jdpicka said:**
> still Firefox refuses to display any pdf documents.

Any ideas would be appreciated.

Unfortunately I don't have any ideas either.  It's annoying having to right-click and save every PDF just to view it.

What I have observed is that if, in Firefox, one goes to Edit, Preferences, Downloads, View and Edit actions, there is no listing for a PDF file, and no apparent way to add one.  This was available before 1.5.0.7, and it's not now.  I'd think there would be a configuration file in Firefox which controlled such things, but I haven't found it yet.

---

### Post by eeried on 2006-11-10
I don't use Acrobat nor the plugin. Xpf or Evince  do the job. If you want to really install a plugin, use mozplugger. It should be all right.

If you don't want to install mozplugger, clicking on a pfdf link will pop a dialog box open in which you'll need to check the option "open the file with" (browse and choose you app, Xpdf or Evince), then tick "always do this". If you're on dial-up better not choose this option for big files -- the file would take a looong while to display.

PS: you can copy selected text from a PDF file using Xpdf (takes some manouvering but it works!). Always best to use libre software whenever it's possible.

---

### Post by rcjhawk on 2006-11-10
> **eeried said:**
>  If you want to really install a plugin, use mozplugger. It should be all right.

Well, last night I found the source of my problem, and it **was** *mozplugger*.  To wit, in my version of mozplugger the first command referring to PDF in /etc/mozpluggerrc was:

 repeat swallow(documentShell) fill: acroread -geometry +9000+9000 +useFrontEndProgram "$file"

which, acroread didn't like.  I only found this out after launching firefox from the command line and reading the error messages.

Two was to fix this:

1) Change the offending line to:

repeat swallow(documentShell) fill: acroread "$file"

which will still open a blank window, but it will also launch acroread (or evince, xpdf, etc., whatever your heart's desire)

2) Remove PDF from mozplugger's command:  comment out or delete all lines in /etc/mozpluggerrc that refer to PDF files.  Quit firefox, and delete the your ~/.mozilla/firefox/pluginreg.dat file.  Restart firefox.  Now when you bring up a PDF file, you get the usual dialog, and the PDF opens with the command of your choice.

Summary:  the version of mozplugger currently loaded with Ubuntu 6.04 has an error in its call to acroread.  Fixing this fixes the problem.

---

