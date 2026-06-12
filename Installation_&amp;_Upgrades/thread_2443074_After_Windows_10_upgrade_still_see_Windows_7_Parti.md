---
title: "After Windows 10 upgrade still see Windows 7 Partition affecting new Ubuntu upgrade"
date: 2020-05-11
forum: Installation &amp; Upgrades
---

### Post by AlyssaVS on 2020-05-11
I'm upgrading to 20.04 alongside Windows 10. The usb installer doesn't give me the option to do that. I am thinking that this is due to an issue or glitch after I upgraded from windows 7 to 10. In the grub menu for some reason there appears to be a windows 7 partition. It doesn't work if chosen and windows 10 works fine. 

I've tried: chdsk, clean disk, and looked at the partitions (all "healthy") on windows side
Not sure what to do from this end. Any ideas?

Alyssa

---

### Post by slickymaster on 2020-05-11
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by AlyssaVS on 2020-05-11
I didn't know it would show up large. I've never posted a photo before. I clicked the "insert image" because it was an option, didn't see an attach function. I just used the "forum" option in imgur and hoped for the best.

Well I tried to fix it by making it an attachment but it appears to have already been done by someone else. I still don't see an attachment function.

---

### Post by slickymaster on 2020-05-11
> **AlyssaVS said:**
> I didn't know it would show up large. I've never posted a photo before. I clicked the "insert image" because it was an option, didn't see an attach function. I just used the "forum" option in imgur and hoped for the best.

Well I tried to fix it by making it an attachment but it appears to have already been done by someone else. I still don't see an attachment function.

I did it for you.

Regarding your doubt, see this: [https://ubuntuforums.org/faq.php?faq=vb3_reading_posting#faq_vb3_attachments](https://ubuntuforums.org/faq.php?faq=vb3_reading_posting#faq_vb3_attachments)

[ATTACH=CONFIG]285821[/ATTACH]

---

### Post by AlyssaVS on 2020-05-11
I didn't see the first line when I posted originally. There were honestly just the two lines. I don't know why. I do see it now.

You've made your point. I think I'll just mark this solved. I doubt anybody will want to help now. SMH

---

### Post by crip720 on 2020-05-11
For your original problem, I would use the 'Something Else" option.  Windows 10 has a fast boot option turned on by default,  turn it off first.  It can interfere with ubuntu seeing partitions well.  Make sure you have at least more than 25 or 30GBs free space, the more the better.  When installing make sure you know which partition is which, people do make mistake often enough to wipe out all data on windows.  Back up for your data safely.

---

### Post by yancek on 2020-05-11
You indicate that you 'upgraded' from windows 7 to windows 10 so that would mean you no longer have windows 7.  Or did you actually install windows 10 in addition to windows 7.  Which is it?

If you upgrade windows 10 and no longer have 7, you may still have the original windows 7 boot files on a separate partition which may be why you see the entry for 7.  Does your Ubuntu boot successfully?

---

### Post by AlyssaVS on 2020-05-11
> **yancek said:**
> You indicate that you 'upgraded' from windows 7 to windows 10 so that would mean you no longer have windows 7.  Or did you actually install windows 10 in addition to windows 7.  Which is it?

If you upgrade windows 10 and no longer have 7, you may still have the original windows 7 boot files on a separate partition which may be why you see the entry for 7.  Does your Ubuntu boot successfully?

Hi. I upgraded from Win 7 to Win 10 as opposed to the installation in addition to Win 7. I was thinking perhaps what I am seeing is a result of that too. Both Ubuntu 18.04 and Windows 10 boot successfully although slow and hang at the load screen longer than before.

---

### Post by AlyssaVS on 2020-05-11
> **crip720 said:**
> For your original problem, I would use the 'Something Else" option.  Windows 10 has a fast boot option turned on by default,  turn it off first.  It can interfere with ubuntu seeing partitions well.  Make sure you have at least more than 25 or 30GBs free space, the more the better.  When installing make sure you know which partition is which, people do make mistake often enough to wipe out all data on windows.  Back up for your data safely.


I had already checked to make sure fast boot is turned off, it was. Thank you for the advice on the "Something Else" option. I was a little worried that if I did that (continue with Ubuntu install) before fixing the Windows partition issue it could break something. I will give it a try.

---

