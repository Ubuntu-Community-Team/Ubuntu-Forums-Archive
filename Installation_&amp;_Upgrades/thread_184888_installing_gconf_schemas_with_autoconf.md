---
title: "installing gconf schemas with autoconf"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by mike2297 on 2006-05-30
I put this in my Makefile.am file:

schemasdir     = $(GCONF_SCHEMA_FILE_DIR)
schemas_DATA     = gnomewotdapplet.schemas

if GCONF_SCHEMAS_INSTALL
install-data-local:
    GCONF_CONFIG_SOURCE=$(GCONF_SCHEMA_CONFIG_SOURCE) \
    $(GCONFTOOL) --makefile-install-rule $(schemas_DATA)
endif

And in my configure.in:

AM_GCONF_SOURCE_2
AC_PATH_PROG(GCONFTOOL, gconftool-2)

This never seems to install gconf schemas to the right place... all other gconf schemas on my dapper install are in /usr/share/gconf/schemas.  However, whenever I make and install my program, they get stuck in /usr/etc/gconf/schemas.

Does ubuntu put schemas in a strange place?  How come autoconf isn't picking up the right directory?

-Mike

---

### Post by groggyboy on 2006-05-30
Have you tried moving all the schemas in /usr/etc/gconf/schemas to /usr/share/gconf/schemas and then replacing the /usr/etc/gconf/schemas directory with a symlink that points at /usr/share/gconf/schemas?

It's not an answer to your question, but it may solve your problem.

---

### Post by mike2297 on 2006-05-31
Well maybe that would help me on my system... but I'm trying to set up my Makefile.am and configure.in files so that it will put the schema files in the right place on anybodys system.

---

### Post by mike2297 on 2006-06-04
bump

---

