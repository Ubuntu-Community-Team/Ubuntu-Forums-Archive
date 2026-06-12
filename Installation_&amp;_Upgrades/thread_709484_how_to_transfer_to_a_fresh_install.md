---
title: "how to transfer to a fresh install"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by DarinB on 2008-02-27
i am a relative newbie,
i have never upgraded i want to do a fresh install of the next LTS and then transfer all my settings, programs and files from the old version. I will buy a new hard drive 250 GB and start fresh.
how would i do this transfer.
I am planning to go from feisty to heron.
what are the steps i would take??????

---

### Post by Sam Lars on 2008-02-27
Back up your home directory, that's your best bet.  Also, if you have done anything special with config files in /etc, etc., you might want to keep them at least for reference.

---

### Post by DarinB on 2008-02-27
Therefore i can simply copy the home folder to the new drive???
what about all the programs i added?
and etc file as well?

---

### Post by Herman on 2008-02-27
:) Hello DarinB, 
I think you should plug the new hard drive into you computer and leave the old hard drive in there as well. It doesn't matter which one is first and which one is second.
Simply install Hardy Heron in the new empty hard drive, it shouldn't affect your Feisty Fawn installation in any way, except it will install Hardy Heron's GRUB to MBR in whichever is your number 1 hard disk. 
Hardy Heron will detect Feisty Fawn and automatically add an entry for Feisty to your new GRUB menu. 
Hardy Heron will also make a mount point and an entry in /etc/fstab to mount your Feisty Fawn installation automatically on each boot-up.

I recommend that you continue to use Fiesty Fawn as your main operating system until Hardy Heron is officially released in April before moving all your files into it. 
Hardy Heron is not ready for general use as your main operating system at this time and some things don't work yet.
When the time comes, it is very simple, just copy your files from your /home/username directory and paste them into your new Hardy Heron /home/username directory.
Then go back into your /home/username directory in  Feisty and click 'View'-->'Show hidden files'. There are some things in .evolution like all your email, addressbook, memos and tasks you can copy and paste into the same folder in Hardy Heron, but you need to start Evolution and configure it in Hardy first.
You'll find your bookmarks and cookies in .mozilla.
There may be some other things you can transfer as well, that depend on what software you have installed.

I don't think it's a good idea to try to install Feisty software in Hardy, that will probably break Hardy, you should install new software in Hardy from the repositories that are in Hardy's /etc/apt/sources.list.

If you want to, you could install a nice program such as 'simple backup restore' and 'simple backup config' in Feisty to make a backup for you.
Then install 'simple backup restore' and 'simple backup config' in Hardy to restore the backup, (or should I say_ transfer _the backup?)

When you are finished you will have plenty of time to check that everything is working well in Hardy and make sure you are happy with it. You can keep Feisty until you are really sure.

Regards, Herman :)

---

### Post by ajeetraj on 2008-02-27
What I would suggest is a bit different from what you exactly asked but I think its gonna help you in future if you want to do the same thing. At the moment, I have divided my hdd allocated to linux into three partitions. I have let's say 40 GB and I have divided it into 29 + 9 + 1. In 29 GB i have created my /home folder and then in 9 GB I have the OS installed and then the 1 GB for ram. Well, I just wanted to give you the idea and then you can just decide about the size by yourself. 

As for me, I just upgraded from Feisty to Hardy and I had a lot of problems. My daemons didn't load from the Kernel then I had to boot from an older kernel, but then I thought if I am trying then why shouldn't I try with a fresh start. I just used the Unet booting as I had windows (I didn't need a CD) and then I have a nice hardy running on my computer...which is way more stable than the upgraded version. 

Hope this helps, 

Good Luck!

---

### Post by DarinB on 2008-02-27
This is exactly the type of help i was looking for you guys are the best!!!!
i will order my new hard drive and when i get it i will get back to the forum.
With this method will it dual boot with feisty?
then will i be able to get rid of feisty completely?

---

### Post by DarinB on 2008-02-27
i am sorry ajeetraj that was a bit over my knowledge base.
i see it is a good idea to have a separate drive or partition for the home folder and the os but the last bit i have no idea what you are talking about.?????

---

### Post by Sam Lars on 2008-02-27
He's saying that he did an upgrade and it had problems, so he did a fresh install and it works much better.

---

### Post by DarinB on 2008-02-27
well i understand that???? thanks but that wasn't my question.
i am planning a clean install on a new hard drive.
and i am thinking now to wait untill it comes out stable 
in the mean time i will plan plan plan.
i have made so many changes to my system as i have now and i didn't document all of them.
i don't even have a list of installed programs.
so i am wondering how to make this less painfull

---

### Post by ajeetraj on 2008-02-27
well, as someone already mentioned before, you can just copy and paste your hidden files from your /home/<user> folder into the new installed system and most of your programs which you were using before will have the same configuration and also, even if you don't have them installed, if the configuration files are there, after the new install your old configurations should work just fine.

---

### Post by Herman on 2008-02-27
When you divide your operating system into separate partitions you are only fencing yourself in and making it impossible for things to be able to expand automatically as your files or your software increases.
Isn't it better to use folders (directories) instead of partitions? They expand and contract automatically on demand, they are always the perfect size. Why force your system to become rigid and inflexible by dividing it up into separate partitions? It only makes thing un-necessarily complicated.

That's just my point of view, there are a lot of power users who will tell you the opposite, but look at both sides and decide for yourself.

Regards, Herman :)

---

### Post by ajeetraj on 2008-02-27
My idea was not to make things complicated but easier for the future. After dividing the hdd, you don't have to worry about anything in the future regarding any new installation or anything...not even your OS screws up completely, because your files will never be touched. Just install any OS in that partition and your data is going to be there for you. So this takes away the tension of having to back everything before every reinstall or anything of that sort. 

also, how does it make things complicated and how does it make your computer slow? I mean when you are saving or using any files from another partition which is mounted as your /home/user then it shouldn't be a problem

---

### Post by DarinB on 2008-02-27
I think i am starting to get it 
when i get the fresh install then i copy over the hidden files therefore even if i don't have all the progams installed it will be ok untill i do.
How about putting the home folder onto a different drive and how do i point to it.
and can i just point hardy to the old feisty home folder that will be on the other drive???
As mentioned above.
will hardy be able to use a home folder created in feisty????

---

### Post by DarinB on 2008-02-27
i also understand the statement of keeping it all on the same partition as intended 
so which opinion is the way to go??????

---

### Post by ajeetraj on 2008-02-27
well, as you know what I am going to say to your second question :) I am not trying to just misguide you or something here. i have the same thing and I have other friends who have the same kind of thing on their computer. 

Well, for the home folder. while installing the OS, you will be asked to do the manual partition where all your hdd partitions will be listed and then just allocate which partition you want to use for what and then you will see it in the option. Just be careful not to chose format the hardrive which is another option there...but just use the "mount as" option and then you are done :)

---

### Post by DarinB on 2008-02-27
so what will the list look like?? is it in g parted or in the set up screen of the os???
meaning what do i choose for what i.e. swap file, primary, blah blah blah it all gets a little muddy for me in my understanding????

---

### Post by ajeetraj on 2008-02-28
The screen looks the same as you install any version of ubuntu. its just that during the install just select the partition where you want your /home folder and then press Enter and then just change the options for that partition just the way you want. i hope this makes sense otherwise, i will have to look for screenshots from somewhere ;)

---

### Post by Herman on 2008-02-28
> My idea was not to make things complicated but easier for the future.:) Yes, I respect you, I realize you are offering the advice that you think is best, we're all on the same side, we all want to help new users get the most enjoyment out of Ubuntu. 
 > After dividing the hdd, you don't have to worry about anything in the future regarding any new installation or anything...not even your OS screws up completely, because your files will never be touched. Just install any OS in that partition and your data is going to be there for you. So this takes away the tension of having to back everything before every reinstall or anything of that sort.  Sorry, but I have to say you still should be making regular backups of at least your most important data to some separate media.
Having a separate /home does not mean your data is completely safe.
>  also, how does it make things complicated and how does it make your computer slow? I mean when you are saving or using any files from another partition which is mounted as your /home/user then it shouldn't be a problemIt won't slow the computer down, I don't remember saying that.
It just makes more partitions that the user needs to manage.
It might not be a problem in DarinB's case since it's only one operating system in this instance.
In computers with more operating systems it can become confusing after a while if each operating system has many partitions that belong to it or are shared. Admittedly, DarinB isn't talking about installing any more operating systems yet, only Ubuntu.
It could make it easier to upgrade to the next version of Ubuntu someday, you are right about that. 
I would be installing the next (future) version again in it's own single / (root) partition and test it first, then transfer the files from one /home folder to new one. 
Do what you like as long as you're having fun.

Regards, Herman :)

---

### Post by DarinB on 2008-02-28
Thank you very much i am getting ideas as to what to do in this case.
One thing for me, it is not just fun (although it is) It is my work (well only on the email and documents level.)
i have all the documents backed up and the rest is my music library about 60GB.
But all in all not just fun>>>
Thanks i do like the idea of easy upgrades but the better file management means a lot to me.
since i was a windows user and even have those stupid windows certsl. 
Managing windows files was just a pain in the ^&*... let alone having to hold my breath when i would power down because it would hang up or the regular crashes, cuz i used borrowed programs, and the nature of the windows beast.
now i am legit and it feels great!!!!!
Thanks again

---

