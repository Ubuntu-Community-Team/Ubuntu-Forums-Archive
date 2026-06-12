---
title: "Key is stored in legacy trusted.gpg keyring confusion"
date: 2023-02-26
forum: Installation &amp; Upgrades
---

### Post by bulgin on 2023-02-26
Hello.  I hope everyone is safe and healthy.

There are multiple examples of how to move keys stored in legacy folders to elsewhere so that apt-get update works rather than throwing errors about "Key is stored in legacy trusted.gpg keyring".  The explanantion in every case are cogent and easy-to-understand except for one big flaw that has me flummoxed.  

Here is an example lifted from one of the many examples:

sudo apt-key export 038651BD | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/slack.gpg

I understand it. Except they never explain how they name - in this case "slack.gpg" - that file?  In some cases the name used - i.e., in this case slack.gpg - is not even in the [FONT=var(--font-mono)]apt-key list results.  

What am I missing?

Any help much appreciated.[/FONT]

---

### Post by &amp;KyT$0P# on 2023-02-26
> **bulgin said:**
> Here is an example lifted from one of the many examples:

sudo apt-key export 038651BD | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/slack.gpg

I understand it. Except they never explain how they name - in this case "slack.gpg" - that file? 

For that method, the name can be anything that ends in ".gpg".  That's the only requirement, but you might prefer to pick a name you personally find descriptive of what you have that specific key installed for.

For more detailed info refer to [FONT=Courier New]man apt-key[/FONT]

---

