---
title: "Reinstall Part 2"
date: 2005-10-10
forum: Installation &amp; Upgrades
---

### Post by Raj on 2005-10-10
**Please note that I did this post at the end of Reinstall...just not many people seem to have picked it up there...cheers**

Hi all,

The timing of this particular thread is amazing. Here goes [darkmatter, I am hoping you are going to be my champion here!! ]

P3-800/128Mb/Hoary

Install was great. Up and running [after major problems with speedtouch 330 ubn modem] about 3 weeks ago. Decided was so happy with it, killed XP [finally].

Since I think i am a little techie in windows, I go and play. install all sorts of WM's/DE's and playing around hacing fun. nice and customised, automounts etc etc. then yesterday i was looking through the index of HOWOT's and found a string of good ones to update firefox to alpha 1/openoffice 2/wine/DC++ etc...

so off I go [dont remember the order]. one of the HOWTO's [could have been the openopffice2 one] seemingly updated my repository list [something like extracting the deb files to a local folder and then adding the extracted files to a self-created Repository folder in my home directory and then pointing the repo's to it - please bear in mind i am completely working off memory here].

anyway - here is the substantive problem. somehow it seems [mr n00b diagnosis here] that it added the Breezy [or at least some Breezy] repo's to my list. Ubuntu tells me there are update, around 200Mb of them. I think this is a little strange, but since i want all the latest update, off we go and download and install.

of couse now the desktop manager crashed and when it drops out to the consol, i notice that rather than it stating it is hoary etc etc, it is saying that the system is ubuntu breezy and wont load X [tried startx - but no go]. did give me a couple of commands to tyr [apt-get commands] but they didnt work.

so i think i have "upgraded" many of the system files to breezy, resulting in a mixed [and fubar-ed] system 

ok, well this *might* have been ok, except i am unable to get online [even in text mode now - although this im a little certain about, as i tried to ping a few sites with no luck, so im thinking thats out]. i luckily [?] had a spare partition [hda1] so i try to install hoary on that. VERY wierd installation process, i think it must have been looking at the current install, but it saw an install of "breezy" and added it to grub. so i still have the old system, with a new one.

questions i have are:

1. possible to recover the original system? if so, how...please?!?!
2. i dont have a separate /home partition so is it possible to move the /home dir from the original install to the new install? if so how? bear in mind that the folders of the users, except for the guest account are password locked. will this be a problem
3. can i transfer all of the settings over? ie monitor/modem/fstab/etc settings? if i can, how will this affect the new system when it tries to use these settings and for example, an app which i installed via apt-get before is not on the "new" system? same with upgrade etc? wont this corrupt the system?
4. if i am not online, the problem is going to be getting on line again, so i can get help from you guys and also start the upgrade/customise process again. any ideas?

i know this has been a long email, but people in forums seem to be more helpful with more detail. also, any idea as to how this could have happened and how to stop it in the future.

if i am able to do all of this, any advice [i have looked at howtos and many threads on backups etc, but i am not very technically savvy and therefore am asking independtly] on how i should set up the drive etc? breakdown is

/had1 = 5gb = "new" install
/hda5 = 5gb = "old" corrupt install
/hda6 = 250mb = swap
/hda7 = 63gb (? approx) = fat32 = data

thanks heaps in advance

raj

---

