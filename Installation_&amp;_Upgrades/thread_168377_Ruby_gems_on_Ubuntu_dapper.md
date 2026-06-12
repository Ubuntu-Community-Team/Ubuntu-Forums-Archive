---
title: "Ruby gems on Ubuntu dapper ?"
date: 2006-04-30
forum: Installation &amp; Upgrades
---

### Post by Hpatoio on 2006-04-30
I've tried everything ... even reinstalled the WHOLE system from the scratch but after have downloaded the latest gem package I write 

"ruby setup.rb"

I get an error that ends with

[INDENT]No library stubs found.

/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require__': no such file to load -- zlib (LoadError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/package.rb:9
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/builder.rb:1
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:61:in `manage_gems'
        from /root/rubygems-0.8.11/./post-install.rb:64:in `install_sources'
        from /root/rubygems-0.8.11/./post-install.rb:75:in `try_run_hook'
        from setup.rb:577:in `run_hook'
        from setup.rb:1315:in `exec_task_traverse'
        from setup.rb:1168:in `exec_install'
        from setup.rb:887:in `exec_install'
        from setup.rb:705:in `invoke'
        from setup.rb:674:in `invoke'
        from setup.rb:1352
[/INDENT]

Now, how do I fix this ?

/Simone

---

### Post by Sef on 2006-05-01
seems like you are missing some dependencies like .rb:21 to start.

---

### Post by Hpatoio on 2006-05-01
yes ... it seems I don't have this zlib library .. 
but I've installed everything related to ruby !

And I think this should be incorporated to the Ruby package ... no ?

How do I install this library ?

Simone

---

### Post by snafu109 on 2006-05-06
Try installing the libzlib-ruby package.

---

