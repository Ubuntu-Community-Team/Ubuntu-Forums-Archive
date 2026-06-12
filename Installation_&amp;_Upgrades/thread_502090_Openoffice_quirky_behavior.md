---
title: "Openoffice quirky behavior"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by revtds on 2007-07-16
I have included below the thread that I have created in the OpenOffice Forum, to help define the problem I have and what has been done to attempt to solve it.

My system is an AMD Athlon, 1G, 1G RAM, was Ubuntu 6.10 , now 7.04, and OpenOffice 1.x, whatever came in 6.10, now 2.2.1 from the OpenOffice site, not the Ubuntu integrated package.
*****
July 11, 2007     I have been using Ubuntu for nearly a year, and the OO suite that came with version 6.10. I have been very happy with it, until one week ago. When I would try to open a file from a week ago, the splash screen would come up, and then I would get a File Recovery screen, with no file name on it. When I would click OK, it would then restart OO and repeat the procedure. When I would try to close the screen, it would just sit there and look at me like I was the dummy!

After reading OO Forum Ubuntu Forum posts for six hours, and trying things like deleting the config files, and the preference files and restarting, I got nowhere. I completely removed and re-installed that version of OO and it did the exact same thing.

In frustration and desperation, I upgraded to Ubuntu 7.04, seeing that it had OO 2.2 included with it. it did exactly the same thing, EXCEPT it now offered to send in a trouble report, but would crash after I clicked Send. Not crash, but freeze, and I would use C/A/Bkspc to restart the GUI.

I then completely removed 2.2 from Ubuntu, having read posts about Ubuntu OO 2.2 being troublesome.

I have installed OO 2.2.1 from files downloaded from OO.org, and I have the exact same problem, EXCEPT I can open files that are older than 2006, but any file saved in 2006 or 2007, will replicate the freeze exactly as it did after I installed Ubunt OO 2.2. 
*****
If one file is not too confidential, you can post it at [http://www.mediafire.com](http://www.mediafire.com) (free and no registration required) or if you prefer you can send it at my e-mail address oooforum.org *at* gmail *dot* com.

*****
That document loads fine for me (OOo 2.2.1 on Fedora Linux).

It seems that all the text is in the "AlBattar" font, which (near as I can tell) is an Arabic font, except your document only uses the Latin alphabet and not the Arabic. Does that make sense to you?
*****
That document loads fine for me (OOo 2.2.1 on Fedora Linux).

It seems that all the text is in the "AlBattar" font, which (near as I can tell) is an Arabic font, except your document only uses the Latin alphabet and not the Arabic. Does that make sense to you?
*****
I was able to open the two files without any problem, so this is good news because it means that the information is not lost. But then I cannot be of further help as I do not use Ubuntu.

Following acknak's post, I have changed the font to a default font, saved the new version and send them to you by e-mail.

Also, I reread your initial post, and it is very strange that older files are readable, while recent files cannot. I imagine there was a change of format from OOo, so I have saved the two files at OOo 1.1 format, (and send them to you as well).
*****
Well, first, thank you both for looking into this. I opened the four files sent back to me, and the first two opened fine. The first spreadsheet opened fine, but slowly, and the second spreadsheet the same.

However, after opening the second spreadsheet, I now have flourescent green highlights aroung all buttons, hyperlinks, the top of the OOForum page is Fl green, and my cursor is Fl green.

Also, text on the bottom of the screen, which tells which window is active has all of the letters shadowed in Fl green and the smileys on the left side of the reply page are all Fl green.

I t also appears that my refresh rate is acting up as windows open and close in quick, jerky movements with Fl green highlights around them as well.

Regarding the AlBattar font, I have no idea about that, as I use Bitstream Vera Sans on the bulletin and Arial on the spreadsheet.

Anything else I can do, please forward ideas or code to me for outputs. While not a newbie to PCs, I am still very low on the learning curve of Ubuntu. 
*****
Many people have reported glitches with the OOo packaged by Ubuntu.

You may have better luck using the package you can download from OO.org directly. Unfortunately, those packages are not set for easy installation on Ubuntu, but I know it can be done.
*****
As I indicated in my original post, I have downloaded 2.2.1, which is not the Ubuntu package, from the OOo website, not Ubuntu's website, and installed it. That is what I am running now. 2.2.1 from OOo. On Ubuntu 7.04. But not the Ubuntu package, the OOo package. The problem started on OOo which came with Ubuntu 6.04, and moving to the OOo package has not helped anything at all.

Any other ideas that I haven't tried?
*****
Sorry, I missed that point, obviously.

Well, for any mysterious OOo problem, I suggest removing (or renaming) the OOo settings directory. OOo seems to corrupt it's settings rather frequently and removing it starts fresh.

On Linux, you can close and exit OOo, then do this (at a command line of course):
Code:
cd
mv .openoffice2 .openoffice2-old

And re-start OOo.
*****
I neglected to mention that I have already created five "other" copies of that file using the "move" command. It made no difference whatsoever. Sorry I forgot to mention that as well.

It seems unlikely that re-installing either the OS or the program would have any effect on this, since it started with 6.10 and OO 1.0, or whatever it was with 6.10, and I am at a complete loss as to where to go next.
*****
Ok, if you've not given up, I'm sure we can clear this up.

The first thing is to establish exactly what the problem(s) is(are), one step at a time.

To do that, you must have a known, stable configuration. If you can, make sure your system is up to date. Ubuntu releases updates ("patches") regularly--do you take advantage of that? Do you have any problems with other applications on the system? E.g., does your browser work well?

Once the system is stable, then make sure you have a stable OOo installed. Again, I would suggest the 2.2.1 from OO.org, which is what you have now, as far as I can tell. Have you checked your package manager to see that all the correct OOo packages are installed, and that no old packages are still hanging around? If you're sure that it's cleanly installed, we'll continue on.

Now, does OOo as installed work correctly with new documents? Can you create a new document from scratch with no trouble? If so, then the problem must be something within your older documents. I would not be surprised if documents created with OOo 1.x cause some trouble, even though they shouldn't.

If you're seeing problems at this point, with a clean install and new documents, then it must be a system-level issue (graphics driver or library, e.g.) and you'll probably need to seek help from an Ubuntu resource.
*****
My system is fully updated at this time, according to Update Manager.


As far as I can tell, the system is stable, Firefox, Evolution, all other software seems to be working normally.

At this point, I have no idea how to know if packages can be removed. I looked in Synaptic at different status indicators, but I don't know what they mean. Some of the ones listed under not installed have 2.2.0 versions on them, so are they removable or are they still part of the system.. How do I find out what is removable and what is not????

If I open new documents, everything seems to be fine. I went back through my files and checked dates and file types, and everything that is OO causes the problem, opening Word and WordPerfect files does not, hence the confusion about some old files killing it and some not. As far as I have been able to determine, ALL OO files will kill it, but Word and WP do not, as well as Excel and PP.

Most of the time now, if I open an OO file from a running OO, (program already open) it gives me a screen to recover "Untitled 1", does so, then asks to send a bug report, which I haven't tried, because that always crashed it before, then gives me a new blank document. If I try to open an OO file from the file browser, then it crashes and loops, constantly giving me a recover document window, time after time. 
*****
Ok, I was wondering if there are remaining components of older versions of OOo that are still installed. It really shouldn't matter, unless the Ubuntu installation is radically different (which is possible), because the OO.org-packaged versions are all independent. A newer version will only see it's own pieces.

Unfortunately, I'm not very familiar with Debian package management, so I can't give you a recipe to try. Let's assume it's ok for now.

Now, what happens exactly when you try to open an existing file--specifically, the file you posted before, "070807bul.odt"?

Was that file made with the older version of OOo, or the new one that's having problems? I ask because it has a recent date.

I'm trying to determine whether your problem is coming from the older file format, or whether OOo just isn't working properly on your system. If it's not working right, then that problem has to be addressed before the file problem.
*****
That file is the last file I made before this problem began.

Each weeks bulletin gets reopened the following week, for continuity of announcements and ease of use for me.

I completed the 070107bul.odt file June 29th, printed and saved it. Monday, 07/02/07, I opened 070107bul.odt to create the bulletin for the 8th, and when the progress bar got halfway across the splash screen, a white window opened up, telling me that for an unknown reason, OO had not opened the file properly, and to click OK to start file recovery.

After clicking OK, the splash screen re-appeared, and the process looped identically.

When I tried to shut down the PC, a small window appeared telling me my session had been saved, and when I clicked OK in that window the process looped again, identically.

The only way I have found to get out of this loop once it starts is CTRL-ALT-BkSPC, which reboots the GUI.

After upgrading to 7.04 and 2.2.1, the only difference is that it actually now tells me it is going to recover "Untitile 1" does so and takes me back to a new working document titled "Untitled 1" which is blank.

This is the case with every OO format file on my PC, (not just Writer) starting in July of 2006, which is when I started using 6.04 and the OO which came with it.

It handles Word and WP files fine.
*****
Sorry, I'm having a difficult time making progress here.

Is OOo starting as part of your session? I.e. when you log in, is OOo starting automatically?

OOo's document recovery is very prone to pointless cyles, where it tries to recover something that obviously doesn't need to be recovered. However, I always see a "Cancel" option whenever OOo prompts during a recovery. It is a little tricky, you have to read and follow the dialog prompts carefully, but you should be able to first "Cancel" then confirm ("Yes") the recovery. Once you have a clear OOo window, just do File > Exit and the next startup should be clean.

Using Ctrl+Alt+Backspace is a bad strategy--only use it as a last resort. In fact, this may well be the root of your problem, and it could affect things other than OOo. It's the equivalent (for your desktop) to pulling the plug out while your computer is running. The tasks that maintain your desktop have the rug pulled out from under them and may not exit gracefully.

You can kill a single application safely using the "X" in the upper right; if the application does not respond, then the system should offer to kill it for you.

If that doesn't work, get a command line and run the program "xkill". That will let you kill a program just by clicking on it's window. There's a Gnome panel applet that does the same thing, called "Force Quit". You probably have to add it to your panel yourself.

Here's a good thing to try: First, create a new user for your system. Again, I can't tell you exactly how to do that, but it should be easy from the system admin menus. Now, log out and log in as that other user. Try running OOo from the new account This will have a completely fresh environment for the desktop and for OOo.

To test a problem document as the other user, you'll have to navigate the File > Open dialog to your normal document directory; you can open the file "read-only". If you try to edit it, OOo will offer to make a copy as the new user.

See how that goes--I think that will shed some light.
*****
OK, here goes:

OO does not start at login

I have never, including today as I double-checked, seen a cancel button option when I get a document recovery window.

Neither will the window go away when I click on the X in the upper right of the window.

I read a post where someone offered the advise of using CAB to restart the GUI when frozen, which indicated it was a perfectly acceptable way out. I have now installed the Force Quit Applet on my panel, which works quite nicely. Thank you for the advice.

I have never been able to get out of the document recovery loop, so I can not do a normal exit of the program at this point.

I created a new user, logged in as that user, open OO, went through the initial screens, attempted to open 070107bul.odt, at which point it did exactly the same as before, including no Cancel button, and no response to the X in the upper right window. Force Quit did work very well. 
*****
Wow. This is really baffling.

CAB is there as a last resort--some times the whole GUI can lock, if for e.g. a program grabs exclusive use of the mouse and then crashes without releasing it. All you can do in that case is CAB. But it really is a last resort.

The only scenario I can imagine, that is consistent with what you describe, is that you are still running an older version of OOo, from before the "Cancel" button was added--at least I think there were some versions released without that. The crash-reporting is one thing that is very different in the distro-specific builds vs. the OO.org builds, so it may be a recent OOo version but the Ubuntu one still.

Unfortunately with OOo, it is very difficult to get specific information about the version and build of the program.

Try these commands (the parts in bold); then copy & paste what you get back here (no need to worry about formatting it like this):
Quote:
$ which oowriter
/usr/local/bin/oowriter
$ oowriter -help 2>&1 | head -1
OpenOffice.org 2.2 680m14(Build:9134)
$ locate soffice.bin
/opt/openoffice.org___/program/soffice.bin
/usr/lib/openoffice.org/program/soffice.bin
$ /opt/openoffice.org___/program/soffice.bin -help 2>&1 | head -1
OpenOffice.org 2.2 680m18(Build:9161)

Note that the green text will be different on your system. Just consistently copy whatever name is printed by the "locate" command. You should see at least one line from "locate" that starts with "/opt"--that's the one to use in the following command.

This should tell us for sure what versions are installed and where to find them.
*****
None of this made any sense, except that it appears to indicate 2.2 is installed.

Below, in each segment is exactly what my terminal screen showed.

tom@tom-desktop:/$ pwd
/
tom@tom-desktop:/$ which oowriter
tom@tom-desktop:/$

tom@tom-desktop:/$ oowriter -help 2>&1 | head -1
The program 'oowriter' is currently not installed. You can install it by typing:
tom@tom-desktop:/$

tom@tom-desktop:/$ locate soffice.bin
/opt/openoffice.org2.2/program/soffice.bin
tom@tom-desktop:/$

tom@tom-desktop:/$ /opt/openoffice.org2.2/program/soffice.bin -help 2>&1 | head -1
OpenOffice.org 2.2 680m18(Build:9161)
tom@tom-desktop:/$
*****
Wow--perfect. Thanks.

So it's completely clear now that only the OO.org package is installed. Thanks for verifying that.

I can only think of two more things to try:

1) Start OOo; do File > New > Text Document. Then, instead of opening a trouble-causing file, do Insert > File. For some reason (that I don't understand), this is more forgiving of glitches in the document. If that works without crashing, save it and then base your new documents on that file.

2) Try running OOo from a command line, like this:
Code:
/opt/openoffice.org2.2/program/soffice

Open a file that causes trouble and see if there are any messages printed in the terminal where you started OOo.

If there are any messages (errors or warnings), post them here. If there are none, then I'm completely out of ideas. My only other suggestion might be to try on the Ubuntu forums, since it really seems to me that the problem is specific to your Ubuntu configuration (e.g. others don't have the same problem opening your file on a different Linux with the same OOo).

Maybe there's some Ubuntu expert, or someone who has solved the same problem, who would see your message and jump in.
*****
Round 10!!!

Using "Insert>File", the problematic files seem to work fine, no glitches or problems.

When started for a command line, and then opening a problematic file, I get the same crash, with a file recovery window, which I attempted, although it listed no file to be recovered, it then went to a blank document and offered to send a trouble report, which I did not do, as this always froze up before.


There was no output whatsoever on the command line, even after closing OO. It just returned me to the prompt.
*****

---

