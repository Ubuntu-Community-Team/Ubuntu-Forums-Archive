---
title: "Migration from Evolution v3.2.0 to Thunderbird v7 [How to - sort of]"
date: 2011-11-04
forum: Installation &amp; Upgrades
---

### Post by nerderello on 2011-11-04
How to migrate from Evolution v3.2.x to Thunderbird v7, well sort of.

I've cobbled together this list of things to as I could not find any answers when I first tried this.

The reason I say "sort of" above, is that there seems to be no 'proper' way of doing this migration completely. If anyone knows a better, more complete way, please post it.

1) I got most of these instructions from here ([http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Migration#Specific_programs%20]("http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Migration#Specific_programs%20")) 

2) The first thing I did was install the add-on to Thunderbird (I'm not going to mention installation or initial set-up of Thunderbird). I downloaded **ImportExportTools-2.6.3.1.xpi** from  [http://nic-nac-project.de/~kaosmos/mboximport-en.html]("http://nic-nac-project.de/~kaosmos/mboximport-en.html") (the download link is near the bottom of that page). Then started Thunderbird, selected **Tools** then **Add-ons**. This brings up a screen that looks very much like the Firefox addons page. Then click on the "**Tools for addons**" icon near the top (screwdriver/spanner icon) of the page and Install add-on from file. Then select **ImportExportTools-2.6.3.1.xpi** and once its installed stop/start Thunderbird. The new addon is now available to you either by right clicking on one of the folders (left hand side of Thunderbird) or through the Tools memu. Please note that (a) this is not the same as the Import tool that comes with Thunderbird and (b) you will need to have selected a folder for the Import mbox file function to work (otherwise it is greyed out).

3) Then I downloaded **jooooooon-maildir2mbox-e47ff64.zip** from [https://github.com/jooooooon/maildir2mbox]("https://github.com/jooooooon/maildir2mbox") and extracted **dateRfc3339ToMbox.pl** and **maildir2mbox** to a suitable folder (in my case this is called bin in my home folder, as I have that setup as part of the path for executables).

4) Next I ensured that both of these new files were executable (right click in Nautilus and check the Permission tab).

5) Almost there, next I amended a line in **maildir2mbox** so that it pointed at **dateRfc3339ToMbox.pl** - line 42 needs to be changed from "**DATE=$(/root/scripts/dateRfc3339ToMbox.pl "$DATE")**" to "**DATE=$(/home/myname/bin/dateRfc3339ToMbox.pl "$DATE")**" , obviously the path (/home/myname/bin/) will need to reflect where you have dowloaded dateRfc3339ToMbox.pl

6) Now comes converting the Evolution mail into the mbox format. I'd like to say that this is easy, but it isn't. 

Evolution keeps mail in the folder **/home/*myname*/.local/share/evolution/mail/local** (yes, there are two 'local' and the first has a fullstop in front to make it hidden). Within there you'll find a **cur** folder that contains every mail under your **Inbox** in Evolution (including those in the Wastebasket/Trash, so empty that out first). And if you're like me, there will be other folders within **/home/*myname*/.local/share/evolution/mail/local** for the main inbox that correspond to sub-folders. For instance I keep all of my emails from my sister in a Evolution folder called Laura (can you guess what my sister's name is? :-). And so there is a folder called **..Laura** (yes, with two fullstops, so it is also hidden). And within the ..Laura folder there is a **cur** folder (ie. **/home/*myname*/.local/share/evolution/mail/local/..Laura/cur**). And it's in this **cur** folder that all of the emails from Laura can be found.

7) To convert the Inbox emails you need to open a terminal and then navigate your way to the /home/*myname*/.local/share/evolution/mail/local/cur folder (obviously your setup won't be called 'myname' and you use the 'cd' command to move between folder (directories), such as 'cd .local' will move you into the .local folder if you're already in your home folder). Once there you need to run maildir2mbox like so - **maildir2mbox > EportedInbox.mbox** . Of course if you haven't saved maildir2mbox into a folder that is in your executable path, you'll have to use something like **/home/*myname*/bin/maildir2mbox > ExportedInbox.mbox**

8 )On my PC this command shoves out a load of errors (**Can't locate DateTime/Format/Mail.pm in @INC.....**), but still seems to work okay.

9 ) You have to run this command for every sub folder, so I had to move from the /home/myname/.local/share/evolution/mail/local/cur (cd ..) folder to the one with my sister's emails (cd ..Laura/cur) - remembering the two fullstops. And then rerun the maildir2mbox command - maildir2mbox > ExportedLaura.mbox

10 ) Once all of the sub folders have been converted (yes, it is long winded isn't it) go back to Thunderbird. Select the Inbox folder (on the left) and then select the **Import/Export** tools (either through the tools menu or by right clicking). Then select **Import mbox** file and then select I**mport Directly one or more mbox files**. A file open dialog box will open, navigate to /home/myname/.local/share/evolution/mail/local/cur for the main inbox and (in my example) /home/myname/.local/share/evolution/mail/local/..Laura/cur for other folders. Each time you're looking for the file created by the maildir2mbox command (ExportedInbox.mbox and ExportedLaura.mbox in my examples). The Import funtion will then create a folder with these names in Thunderbird with the emails in them. You can of course then move the emails and folders around within Thunderbird (use F2 to rename them them as you wish).

11) The rest of the migration is as per ([http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Migration#Specific_programs%20](http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Migration#Specific_programs%20)) and no, I haven't found a way to migrate my email rules/filters, they have to be re-created.

Having done all of this, I've decided to stay with Evolution as I still prefer it.

Hope that this has helped and like I said as the biginning, if you know a better way PLEASE POST IT.

---

### Post by nerderello on 2011-11-04
I've just been shown a different script in [http://yergler.net/blog/2010/06/06/batteries-included-or-maildir-to-mbox-again/#file-maildir2mbox.py]("http://yergler.net/blog/2010/06/06/batteries-included-or-maildir-to-mbox-again/#file-maildir2mbox.py")

This does the same conversion job shown above (by dateRfc3339ToMbox.pl and maildir2mbox), but without the error messages, need for editing and is a little bit cleaner in use.

So, if its saved to the bin folder in my home folder it is used by:
> [FONT="Courier New"]$ python ~/bin/maildir2mbox.py ~/.local/share/evolution/mail/local/..Laura  ~/.local/share/evolution/mail/local/..Laura/newLauraExport.mbox[/FONT]

ie. python (which is the language it is written in) followed by the path and name of the script, followed by the path to the folder that contains the 'cur' folder, followed by the name you want to give the mbox file (it is all one line, but has been split in the forum). 

The rest (importing etc.) is the same as above.

---

