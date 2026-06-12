---
title: "&quot;aptitude search&quot; shows packages as not installed"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by street spirit on 2012-02-17
I'm having trouble with aptitude: both the "firefox" and "php-apc" packages are installed, but don't show up as such in a package search via aptitude:

```

$ aptitude show firefox | grep State
State: [COLOR="Red"]installed[/COLOR]

$ aptitude search firefox | grep "  firefox "
[COLOR="Red"]p[/COLOR]   firefox        - Safe and easy web browser from Mozilla

```

Interestingly, if only one package matches the search, its state is displayed correctly:

```

$ aptitude show php-apc | grep State
State: [COLOR="Red"]installed[/COLOR]

$ aptitude search apc | grep php-apc
[COLOR="Red"]p[/COLOR]   php-apc        - APC (Alternative PHP Cache) module for PHP 5

$ aptitude search php-apc
[COLOR="Red"]i[/COLOR]   php-apc        - APC (Alternative PHP Cache) module for PHP 5

```

I'm running Kubuntu 11.10, fully updated. This is a laptop, and I normally use Apper to apply updates, but I had a couple of weird failures there lately, which may be related.

Any ideas?

---

