---
title: "Can an upgrade 2 versions from the current be done and not reformat the drive?"
date: 2016-04-19
forum: Installation &amp; Upgrades
---

### Post by Shobuz99 on 2016-04-19
Hello all,
I've searched this forum and could not find the answer.
Briefly, I am running 14.04.3 LTS Trusty on my Dell Inspiron 1525 160GB HDD laptop.
It literally took me years to move off 10.04 LTS and get a better distro.
When I decided to do that, I assumed that I couldn't go from 10.04 to 14.04 without doing a back up, and reformatting the 80GB drive.
So I did a clean install of 14.04 on an empty 160 HDD and then connected the 80GB drive externally, by USB,
and transferred a load of files to the new drive and the newer Ubuntu 14.04. Very time consuming.
However, I noticed when I upgraded to 14.04 LTS that there was a 15.04, a 15.10 and a 16.04beta that exist beyond 14.04!!
I thought, well, I'll upgrade to one of those someday, when I get a new 250GB drive and then I'll have to do the data transfer thing all over again.

That day has arrived. My 250GB SATA drive is being shipped to me as I type this and I expect it any day now.

My first question is: Can an upgrade, 2 or 3 versions higher than the current be done and not require a reformat of the original drive?
Second question:    Am I going about this the long way or the dumb way or otherwise wrong way?
Third question:       Are there Ubuntu tools that can make all this easier?

I'd like to use a more streamlined method of upgrading Ubuntu when it's time, and preserving my data and backups.
I'd like some suggestions. I'm open to change, I just need to be sure of myself when I commit to a big change.

Shobuz99

---

### Post by Bucky Ball on 2016-04-19
1/ Yes, with a caveat. LTS versions can upgrade directly to the next LTS, e.g. 14.04 LTS to 16.04 LTS, leapfrogging the interims in between. This normally can't be don't through the Software Updater until after the first point release of the new LTS, but it can be done using a terminal.

Interim versions can only upgrade to the next release.

2/ Which bit exactly?

3/ See question 2. All depends on 'it'. ;)

---

### Post by Shobuz99 on 2016-04-19
> **Bucky Ball said:**
> 1/ Yes, with a caveat. LTS versions can upgrade directly to the next LTS, e.g. 14.04 LTS to 16.04 LTS, leapfrogging the interims in between. This normally can't be done through the Software Updater until after the first point release of the new LTS, but it can be done using a terminal.

Interim versions can only upgrade to the next release.

2/ Which bit exactly?

3/ See question 2. All depends on 'it'. ;) 

Excellent answers ALL! Thank you. I'll skip worrying about #2 and #3 andd wait for 16.04 to reach LTS.
Once that happens and I upgrade without risk of erasing accumulated data, I will create an image of that drive,
and then format the new 250GB, partitioned, and copy the image from the 160GB drive that has the upgraded 16.04 LTS.

Does that sound like a good plan? Am I missing any obvious steps?
I would also like to know the recommended Ubuntu supported software that does "imaging" of a drive or partitions that can be made into an .iso.
Would Brasero work for this purpose?

Shobuz99

---

### Post by yancek on 2016-04-19
You can't upgrade 'without risk of erasing accumulated data', there's always a risk so you need to have backups.  A power loss in an upgrade will really mess things up.

---

### Post by Shobuz99 on 2016-04-19
> **yancek said:**
> You can't upgrade 'without risk of erasing accumulated data', there's always a risk so you need to have backups.  A power loss in an upgrade will really mess things up.
Thank you. Yes, I realize that. You are correct. It is a habit everyone must be into, by now.
My intention is to make a backup image, before I begin the upgrade. 
Once the upgrade is complete, I no longer worry about the accumulated data. 

Sbobuz99

---

### Post by Shobuz99 on 2016-04-22
My next plan is to find a HDD Imaging program on the Synaptic Package list that will let me create the HDD image from my existing drive with 14.04 LTS, 
so I can burn a disk with that image for a backup. Then, I plan on installing that full image on my 250GB HDD. 
When 16.04 becomes LTS, I plan to upgrade from 14.04 LTS to 16.04 LTS and hope nothing goes wrong.

So I'm asking for a recommendation on which Imaging program is a good choice. 
I've heard of Clonezilla; but the Synaptic Package has multiple choices to choose from.
Any feed back here would really help me to go forward..

Thank you for your continued help.

Shobuz99

---

### Post by Bucky Ball on 2016-04-22
I use Clonezilla or fsarchiver. 

I have one entry for Clonezilla in Synaptic.

---

### Post by Shobuz99 on 2016-04-24
> **Bucky Ball said:**
> I use Clonezilla or fsarchiver. 

I have one entry for Clonezilla in Synaptic.

I've looked at both Clonezilla and fsarchiver on synaptic. I get the feeling that they don't operate the same way. 
That is, fsarchiver seems to be for file systems and doesn't include data files; such as folders that have been created since install of the distro.
Is that correct, or am I misunderstanding what fsarchiver does?

Clonezilla looks a little bit confusing to me, too. I saw the website for Clonezilla and there were some options
that I wondered whether i would know the right ones to choose, as I began the backup.

I suppose I should pick a package, install it, and try it.
I just don't want to make any fatal errors that put me in a mess of my own making.

Thank you for indulging me Bucky Ball. I'm just being cautious. :)

Shobuz99

---

### Post by Shobuz99 on 2016-04-26
I have another question. The existing 160GB that has 14.04 LTS boots to require an encrypted passphrase, for sda5_crypt. 
It's an option I chose to use when I installed 14.04 from Ubuntu "Live".
When I clone the image for backup, does the encryption remain intact?
If not, do you know whether Clonezilla will offer an option to restore the encrypted passphrase?

Shobuz99

---

### Post by Shobuz99 on 2016-04-28
I'm voluntarily closing this thread. I've backed up my drives, and have bootable CD of 16.04 and my 250GB drive.
However, I'm waiting to decide if I want to use Clonezilla on the 160GB drive and burn a CD image of it, for safe keeping,
Or simply put the image on the new 250 drive and then upgrade to 16.04.1 when it becomes available.
I ordered some memory for my Dell 1300 and I intend to upgrade that from 10.04 to at least 14.04 for now.
Since I'm not finished deciding on the final outcome, I don't think it's fair to leave this open and hanging.
You've answered my questions and I thank you for the advice and help.

When I get all these plans solid and actually move forward, i will create a comment on the thread about upgrades
"Upgrading from 15.10 to 16.04 - How'd it go?" and just tell what I did and if it worked out. ok?

Thanks again for your help, Bucky Ball. :-)

---

