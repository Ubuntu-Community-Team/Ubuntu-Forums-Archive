---
title: "[SOLVED] HOWTO obtain stats related to overall installation"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by rshetye on 2008-08-26
e.g. doing an apt-get install or apt-get remove yields,

**(Reading database ... 104905 files and directories currently installed.)**

How do I get this information in bold without doing an install or a remove?

thanks.

--- edit ---
wrote a script to do this

**dpkg-stats.rb**
```
#!/usr/bin/env ruby

# $DEBUG=true
# $VERBOSE=true

=begin
Copyright: Ranjeet Shetye (ranjeet@shetye.com). 2008
Licenced under GPL-2.

1. Output must list the files and directories installed by apt, and the files/dirs missing (e.g. due to localepurge)
2. Get the info for all installed packages from the dpkg db
3. Add each entry into a hash array for dirs, or a hash array for files, if the entry does not already exist in the corresponding array
4. Multiple references to dirs are ok
5. Multiple references to files are not ok, should be flagged
6. If the listed file/dir does not exist on disk, not ok, should be flagged
7. Print out all the details!!
8. ???
9. Profit!

ps: for testing purposes, use Dir.glob for q*.list rather than *.list, its easier to deal with a much shorter list

=end

class DPkgStats
    def initialize
        @dirhash=Hash.new
        @filehash=Hash.new
        @filecount=0
        @dircount=0
        @missingcount=0

        @md5sums_based_filecount=0
    end

    def list_based_info
        Dir.chdir("/var/lib/dpkg/info");
        Dir.glob("*.list").sort.each \
        { |packagename|
            # puts packagename
            File.new(packagename, "r").each \
            { |singlefilename|
                singlefilename.chomp!
                # puts " #{singlefilename}";
                begin
                    if (File.ftype(singlefilename) == "file")
                        if (@filehash.has_key?(singlefilename) == TRUE)
                            puts "Warning: file #{singlefilename} in #{packagename} has been encountered in #{@filehash[singlefilename]}"
                            @filehash[singlefilename] += ", " + packagename
                        else
                            @filehash[singlefilename] = packagename
                            @filecount+=1
                        end
                    else
                        if (@dirhash.has_key?(singlefilename) == TRUE)
                            # puts "Warning: directory #{singlefilename} has been encountered earlier"
                            # @dirhash[singlefilename] += 1
                        else
                            @dirhash[singlefilename] = packagename
                            @dircount+=1
                        end
                    end
                rescue Exception=>e
                    # Errno::ENOENT
                    # puts "Exception #{e} #{singlefilename}"
                    # puts "Exception #{e}"
                    @missingcount+=1
                end
            }
        }
        puts "dircount = #{@dircount}"
        puts "filecount = #{@filecount}"
        puts "missingcount = #{@missingcount}"
    end

    def md5sums_based_info
        Dir.chdir("/var/lib/dpkg/info");
        Dir.glob("*.md5sums").sort.each \
        { |packagename|
            # puts packagename
            File.new(packagename, "r").each \
            { |singlefilename|
                # puts " #{singlefilename}"
                @md5sums_based_filecount+=1
            }
        }
        puts "md5sums_based_filecount = #{@md5sums_based_filecount}"
    end
end

dpkgstats = DPkgStats.new
dpkgstats.list_based_info
dpkgstats.md5sums_based_info

```

---

### Post by lackoblacko on 2008-08-26
sudo synaptic 

to see all packages installed.

---

### Post by Kevbert on 2008-08-26
You can get a list of all installed packages with the command:
```
dkpg --list > pack.txt
```
Now using Nautilus go to your home directory and double click on the resulting file pack.txt to view the package list.

---

### Post by rshetye on 2008-08-26
thanks guys, but I am specifically looking for the command that will provide the number of installed files and directories, without any install/remove operation.

---

