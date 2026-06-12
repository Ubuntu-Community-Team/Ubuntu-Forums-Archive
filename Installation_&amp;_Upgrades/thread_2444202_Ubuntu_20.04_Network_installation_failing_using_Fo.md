---
title: "Ubuntu 20.04 Network installation failing using Foreman and internet repos"
date: 2020-05-26
forum: Installation &amp; Upgrades
---

### Post by ub-newbie3 on 2020-05-26
Greetings,

I am getting "No kernel modules were found" while trying to install Ubuntu 20.04 using Foreman & Internet repo. If I use same settings for 18.04 (foreman & internet repo), it works. I have attached error screenshot as well.

Please let me know if I am missing something or if Ubutnu 20.04 is not yet ready for network based installations. Also, I could not find netboot.tar.gz file for this release (as of mid-May 2020). 

Hope to get some solution/workaround from those who are successfully able to install Ubuntu 20.04 using network install. :)

Cheers..

[IMG]https://photos.google.com/share/AF1QipNJbGq9EA-Ym9UMCCtHzhhKSrxedvRrmjRcNYxEsd2y_YHqb2HKs55PDubCikIcVg?key=MTduVkZhUTMyWDh1Z2U3MjJEb0Q5dkZGRGtad2JR[/IMG][IMG]https://photos.google.com/share/AF1QipNJbGq9EA-Ym9UMCCtHzhhKSrxedvRrmjRcNYxEsd2y_YHqb2HKs55PDubCikIcVg/photo/AF1QipNo7c6RC3YCEmzqMLYMOv6Tew8YeyHW2sEyj04C?key=MTduVkZhUTMyWDh1Z2U3MjJEb0Q5dkZGRGtad2JR[/IMG]

---

### Post by DuckHook on 2020-05-27
Welcome to the Forums, ub-newbie3

Does Foreman support Focal yet? When you use a provisioner like Foreman, you are largely giving up independent fine-grained control and relying on them to provide the functionality. It cannot install what it does not yet support.

Perhaps you can contact Foreman for advice. They also have a forum site here: [https://community.theforeman.org/c/community](https://community.theforeman.org/c/community)

Their community would naturally be far more knowledgeable about their own product than we are here.

Of course, if you bypass Foreman, you can install directly from whichever *official* mirror is nearest you, but then, you would be nerfing Foreman. As for upgrade timing, note that if you are going from LTS to LTS, Ubuntu is designed to not upgrade until the first point release sometime in July. This is a good conservative strategy. My own forced upgrade has revealed a number of bugs that I've had to either solve or work around. A lot of these will likely be squashed by the first point release, so waiting for that would be wise, especially if yours is a production machine.

---

### Post by ub-newbie3 on 2020-05-28
Hello,

Thanks for your reply and you are right - I was trying it on Foreman 1.20.3 version. After your response, I tried it on a later version (Foreman 1.24.3) and it worked and now I am able to install Ubuntu 20.04.

thanks! :)

---

### Post by DuckHook on 2020-05-28
Glad it's all worked out for you.

I have already marked your thread "solved". In future, please mark solved threads using the "Thread Tools" drop-down so that others looking for solutions can benefit from yours.

Good Luck and Happy Ubuntu-ing.

---

