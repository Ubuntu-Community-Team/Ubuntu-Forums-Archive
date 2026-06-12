---
title: "Impossible upgrade 23.04 -&gt; 23.10 -&gt; 24.04"
date: 2024-09-19
forum: Installation &amp; Upgrades
---

### Post by giampisalvi on 2024-09-19
I have a laptop with Ubuntu 23.04 that I haven't used for a while. Now I would like to upgrade it to 24.04. When reading the forum, I understand that in order to upgrade to 24.04 I first have to upgrade to 23.10. However:
1) I cannot get update-manager to show 23.10 as an alternative (has it already expired in September 2024?)
2) update-manager incorrectly shows 24.04 as an option for upgrade, but when I agree to perform the upgrade I get an error message:
------
Can not upgrade


An upgrade from 'lunar' to 'noble' is not supported with this tool.
------

I tried:
0) upgrading all packages to the latest available for 23.04
1) changing the "Notify me of a new Ubuntu version" to any of the alternative options,
2) downloading the Mantic (23.10) files manually (following an old forum post)
to no avail.

Am I stuck with 23.04? Any chances of being able to eventually upgrade to 24.04?
When checking for duplicate posts, please check the date, because most of forum posts on the topic are from a time when 23.10 was not officially released yet, but now we are in September 2024.

Thank you!
Giampiero

---

### Post by yancek on 2024-09-19
Support for 23.10, like all non-LTS releases if for 9 months so yes, there repositories are not located where they once where and will not be available with the standard methods.  They should/might be available in ubuntu archives if you want to do an online search for that and then attempt the process but it would be much simpler not to mention faster, to just do a fresh install after backing up any personal data on the machine.  The problem with what you want to do is to upgrade from an unsupported release (23.04) to another unsupported release (23.10) before updating to a current release.

---

