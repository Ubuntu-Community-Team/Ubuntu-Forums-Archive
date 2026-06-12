---
title: "W3C Markup Validator"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by ryneezy on 2006-10-04
I installed the Dapper w3c-markup-validator package for my coworker because she wrote a utility to use the w3c-markup-validator to verify our entire site conforms to standards.

However the Dapper w3c-markup-validator is version 0.6.7 and her utility uses the direct input method found in version 0.7.x.

Since there's no w3c-markup-vaidator package using version 0.7.2, I'm trying to install it manually but I'm having some trouble. I went through all the steps in found in the documentation at <http://validator.w3c.org/docs/install.html>, but I get an error when I try to enter HTML into the direct input and all other input methods.

The error is:
```

Configured SGML Parser '' not executable! at /usr/share/perl/5.8/CGI/Carp.pm line 314.
BEGIN failed--compilation aborted at /usr/lib/cgi-bin/check line 192.

```

So it looks like I do not have all the Perl prerequisites.

I tried getting the Bundle-W3C-Validator from [http://search.cpan.org/dist/Bundle-W3C-Validator/](http://search.cpan.org/dist/Bundle-W3C-Validator/)

Then running the command:
```

sudo perl -MCPAN -e "install Bundle::W3C::Validator"

```

Everything goes fine until I get the error message:
```

Bundle summary: The following items in bundle Bundle::W3C::Validator had
installation problems:
  CGI Config::General HTML::Parser HTML::Template Net::IP Set::IntSpan 

```

What am I doing wrong?

---

### Post by ryneezy on 2006-10-09
So I ended up using the package from the Debian project w3c-markup-validator 0.7.2 marked for testing.

It installed and it's working quite well. I didn't need to install it from source afterall.

---

