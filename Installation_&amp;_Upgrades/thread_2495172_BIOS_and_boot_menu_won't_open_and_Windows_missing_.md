---
title: "BIOS and boot menu won't open and Windows missing after Ubuntu dual-boot"
date: 2024-02-09
forum: Installation &amp; Upgrades
---

### Post by get-some-gyan007 on 2024-02-09
Hey everyone,


I recently tried to set up a dual-boot with Ubuntu alongside my existing Windows 10 installation. Unfortunately, I'm running into some major problems:



[LIST]
[*]BIOS Inaccessible: I can't access my BIOS settings at all. The usual keypresses during startup aren't working.
[*]No Boot Menu: I can't select a different operating system at boot.
[*]Missing Windows: It seems like my Windows installation might be gone, as Ubuntu loads immediately on startup.
[/LIST]

I've tried finding fixes online, but my laptop seems determined to make things difficult. [Some websites]("https://newseum.co.in/bios-not-working-after-dual-boot-how-to-fix/") suggested giving this forum a try, so here I am hoping for some tech wizardry!
Has anyone else experienced this after a dual-boot? If so, I could really use some troubleshooting tips to get my Windows back and make my BIOS reappear. Thanks so much!

[IMG]https://filestore.community.support.microsoft.com/api/images/17324aa4-01e2-4a95-ba6f-79be565118dd?upload=true&fud_access=wJJIheezUklbAN2ppeDns8cDNpYs3nCYjgitr%2BfFBh2dqlqMuW7np3F6Utp%2FKMltnRRYFtVjOMO5tpbpW9UyRAwvLeec5emAPixgq9ta07Dgnp2aq5eJbnfd%2FU3qhn54%2F%2BybexgGEoQ%2FMo9buEA9DjvMdNCcsSh67cUhZAcnxKcw0Uc2nfH7Td4XVJJMPvG73nEeUP9gxiUz6oAmCQteF4k%2B32AulP89cJfHp3QtoRd2t7xlHNIWvYV6rxiTwW0JHnWxsGX7jL093J34R8P6KRhcwy9FWUW%2F9EqQ2VwxaOJ6wUSPOFyoYCJXx%2Bl8A7Aok4XwMUwinGH5k%2FaZjlZjcDfHl%2BCmvsTCgl2JZiD4gpFxsFaozBn7HXmpH%2BRlvRphHQ3BW4eg0uie6sF1aqFZBXg32lN5ybQ8pRQ%2FC%2FgGs7c%3D[/IMG]

---

### Post by tea for one on 2024-02-09
> **get-some-gyan007 said:**
> BIOS Inaccessible: I can't access my BIOS settings at all. The usual keypresses during startup aren't working.
As you can access Ubuntu, open a terminal and enter:-
```
sudo systemctl reboot --firmware-setup
```
While in your firmware settings, disable Secure Boot, Fast Boot , TPM and other security features.
> No Boot Menu: I can't select a different operating system at boot.
Possibly Windows 10 was hibernating when you installed Ubuntu?
Boot Windows 10 via your PC boot menu and disable hibernation i.e. fast start up

Windows will be added to grub if it is not in hibernation state.
Reboot into Ubuntu, open a terminal again
```
sudo update-grub
```
Any joy?

---

