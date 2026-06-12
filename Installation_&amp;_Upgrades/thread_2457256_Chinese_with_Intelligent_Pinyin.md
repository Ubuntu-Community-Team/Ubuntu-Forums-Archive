---
title: "Chinese with Intelligent Pinyin"
date: 2021-01-28
forum: Installation &amp; Upgrades
---

### Post by sebastian-heiden on 2021-01-28
On my new laptop preinstalled with an Ubuntu Budgie derivative in Version 20.04. The first local is German. I wanted to add Chinese via "**Region and Language**" I selected "**Intelligent Pinyin**", which worked only half way for me. The suggested characters aren't shown.
But I still can write the Chinese characters and select them via the numbers, I just don't now what I select (without the suggestions).
In the intelligient Pinyin tab the Suggestions box is activated. I also can write, the Chinese sentence ending marks.
Steps taken:

I restarted the systems, several times.
I removed and re added Intelligent Pinyin. (but seams like the settings are only deactivated not deleted. After re adding it, the settings were the same non default settings as before)

Are there some settings I can change via console, to repair the Pinyin?

---

### Post by CelticWarrior on 2021-01-28
Welcome.

Here are two methods, one works brilliantly, the other not so much: [https://www.pinyinjoe.com/linux/ubuntu-18-gnome-chinese-setup.htm](https://www.pinyinjoe.com/linux/ubuntu-18-gnome-chinese-setup.htm)

---

### Post by ping-wu on 2021-01-29
Try deleting the $HOME/.cache/ibus/libpinyin folder, then restart ibus-libpinyin.

---

### Post by sebastian-heiden on 2021-01-29
@CelticWarrior

Thanks for the links, thats what I did, too. I but thanks to the link I  added Chinese Taiwan (Chewing with Pinyin), too.

@thanks at ping-wu, I tried that. deleting and than restarted the ibus, It didn't work. It was the same as before. Therefore I, removed Intelligent-Pinyin from Region & Languages and then removed it, restarted the gadget and than readded Intelligent Pinyin. But it still was the same.

Also for Chinese-Taiwan (Chewing) no surgestion is show. So is it a more genereal problem, with ibus?
Edit: FCITX- doesn't work as I am used to, because the config tool is not found.

Edit: When I installed xubuntu-dektop side by side, than I got intelligent pinyin running with no problem on the way. But when I activate intelligent pinyin  some extra config icons are shown. On Budgie desktop (same Laptop) nothing changed, no suggestions, no extra icons.

---

