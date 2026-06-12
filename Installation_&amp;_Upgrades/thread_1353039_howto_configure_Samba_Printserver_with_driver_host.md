---
title: "howto configure Samba Printserver with driver hosting"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by maulbongo on 2009-12-12
Samba Printserver using Ubuntu.

I'm wrinting this howto, because there are still the questions why it is not possible to copy the drivers to the server and the printer configuration is greyed out in windows.

This howto is written for GUI users, although nearly everything is also working within the terminal.

I asume that Ubuntu is already configured and running functional within the network.
I configured and tested this using Ubuntu 9.04 (jaunty) 64bit.

At  the moment I'm testing Ubuntu 9.10 (karmic) 64bit, but I still got some problems, which I'll explain later.

1.

Configuring Cups (System/Administration/Printing)

Click at upper left  &#8222;Server&#8220; and then &#8222;settings&#8220;.
Here I checked everything, instead of &#8222;Show printers shared by other systems&#8220; and
&#8222;Allow users to cancel any job (not just their own)&#8220;.


2.

A printer has to be created (I guess you can handle this without my help).

3.

Samba should be installed and there is a great and simple tool for configuring Samba, system-config-samba,  because you don't need more for this purpose.


4.

Now start the Samba Tool (System/Administration/Samba).

I asume, that the workgroup has been configured with this tool matching the actual domain or workgroup you are using (Preferences/Server settings/Basic)
After this create an user (Preferences/Samba User):



I chose  root  (Unix Username) and also as Windows Username root  and set the passwords (in this case I chose the same I use for the Ubuntu login).

5.

To be sure that there won't be any conflicts, I also edited the Print$ share:


I switch the share to writable, don't get cross eyed, the tool shows that the share is already writable, although it isn't. So uncheck writable and check it again, now it is writable.

Then also change following on the tab &#8222;Access&#8220;:


&#8222;Allow access to everyone&#8220;.
This isn't save, some would say. Now everybody could write in this folder, but it's working and the &#8222;nomal&#8220; Windows User don't know this dollar-share at all ;). Who want to have it more safe could restrict it, but then I can't say if all is working correct.

6.

Now lets go on with a windows system, here I use a Windows XP with SP3.
Within the network choose the Ubuntu-Printserver.
And go to the share printers and faxes.
There you now can see the printers like in this example, I named my printer test01.



6.

Now do a right click on this printer and choose &#8222;properties&#8220;.
A message appears: &#8222;The &#8222;&#8220; is not installed on this computer. Some printer properties will not be accessible unless you install the printer driver. Do you want to install the driver now?"
It is important to click &#8222;No&#8220;.

7.

Now the Printer configuration window opens, in my example it is cutted a bit, but you can see that all is greyed out and you can't administrate the printer. Thats the problem a lot of people have got.
The reason is, that at this point no authentication happens to the Sambaserver. 


8.

For fixing this problem we go back to the Ubuntu system, open Nautilus and set a folder shared (here for example &#8222;Öffentlich&#8220;). Just check &#8222;Share this folder&#8220;!


Sharing this folder is only for authentication purpose of the administrative windows client.

9.

We go back to the windows system. here we go to the shared folder of the Ubuntu system and voila, you'll be asked for User and Password. There enter &#8222;root&#8220; and the corresponding password.
Now this folder can be accessed.
To be sure that everything is working you can go to terminal in Ubuntu (Applications/Accessories/Terminal) and enter the command &#8222;sudo smbstatus&#8220;, ther now should be &#8222;Username&#8220;, &#8222;Group&#8220; and &#8222;Machine&#8220; filled and also under &#8222;Service&#8220; should be &#8222;Öffentlich&#8220; visible (like in this screenshot).
The command &#8222;/etc/init.d/samba restart&#8220; you should remember it often helps out ;)



10.

Now it is time to go back to the windows system and do a right click on the printer and choose &#8222;properties&#8220; again.
You can see that nothing is greyed out anymore and you can administrate the printer.



11.

Now we can add the driver, but unfortunately when finishing an error message appeares:
&#8222;Printer driver %name% was not installed. Access is denied.
.


This tells us that we can access print$ of the Ubuntu Servers but don't have write access there.

12.

We go on the Ubuntu system to the folder of this share print$ (/var/lib/samba/printers) (I do this with Dolphin, because it definitely sets all rights correct to the subfolders and files. Nautilus not always is doing this) and set rights for &#8222;Owner&#8220;, &#8222;Group&#8220; and &#8222;Others&#8220; to &#8222;Can View & Modify Content&#8220;. And also check &#8222;Apply changes to all subfolders and their contents&#8220;.


14.

Repeat step 11. And now the driver should be copied without any problems to the server.


15.

Now we again can go to the printers properties. There go to the tab &#8222;Advanced&#8220; an click the button &#8222;Printing defaults&#8220;. Then click the button &#8222;Advanced&#8220; and here you can switch papertype from Letter to A4 or any setting you need.


Thats it now you can add more printers and drivers this way.
If you add a printer in Windows, you now get all driver via the Ubuntu Samba Server and you don't have to install them manually.

With Ubuntu 9.10 there are still some problems which I couldn't fix.

jaunty uses &#8222;samba 2:3.3.2-1ubuntu3.2&#8220; and &#8222;cups 1.3.9-17ubuntu3.4&#8220;. karmic instead uses &#8222;samba 2:3.4.0-3ubuntu5.2&#8220; and &#8222;cups 1.4.1-5ubuntu2.1&#8220;.

Here you have to pay attention for this:

First of all another folder has to be created in /var/lib/samba .
This I named  prnproc. The share HAS TO BE named prnproc$ .
Set the rights like they are set for print$ (in Samba, and also for the Filesystem).
In this folder there also will be drivers stored.

And there are other problems for example

The same printer with the same drivers is not working correct. (Screenshot).


These settings are openend on an non administrative client.
On the leftern side the printer shared on Ubuntu 9.04, on the rightern side the same printer shared on Ubuntu 9.10.
You can see that even settings made by the administrative client are not set correct. The Paperunits for example are set to &#8222;not available&#8220; (&#8222;Nicht verfügbar&#8220;).
If you change the rights for this printer for &#8222;everybody&#8220; to allow &#8222;Manage Printers&#8220;.

You can see that the Paperunits are shown, but Paperunit2 for example is set to A4 instead of A5, even if you set it manually within this client it alway jumps back to A4.


And the Paperunits are also not used correctly the Paper is alway taken out of the first Unit.

Another problem I found out using Ricoh printers.
In my company we use a MP C3500.
With Ubuntu 9.04 there are no problems.
But using Ubuntu 9.10 as Server you even can't do a Testprint as soon you have activated the accessories (Finischer, etc.).


On the leftern side again Ubuntu 9.04 and on the rightern side  9.10

When printing the testpage an error message appears:
&#8222;The test page could not be printed. Should be shown the printing problem help page?" 

With all those difficulties I will be using Ubuntu 9.04 (jaunty) as Printserver.

If someone has fixes for those error, please write.

I hope this howto is understandable.

Manual with pictures:

[http://rapidshare.com/files/319882035/samba_print_server_howto-eng.pdf.html](http://rapidshare.com/files/319882035/samba_print_server_howto-eng.pdf.html)

---

