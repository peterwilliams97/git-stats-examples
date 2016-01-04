# git-stats-examples
Examples for the [git-stats](https://github.com/peterwilliams97/git-stats) repository.  This repository currently contains one script [code-age.py](https://github.com/peterwilliams97/git-stats/blob/master/code-age.py).

code-age.py analyzes the age of files in a git repository and writes some reports and draws some graphs about them.

It writes reports in the directory structure given in [git.stats.tree.txt](https://github.com/peterwilliams97/git-stats/blob/master/examples/git.stats.tree.txt)

NOTE: __LoC__ is short for Lines of Code.

e.g. For repository [cpython](https://github.com/python/cpython.git)

    [root]                                    Defaults to ~/git.stats
      └── git                                 Directory for https://github.com/git/git.git
          └── reports
              └── 2015-12-29.28274d02.master  Revision 28274d02 which was created on 2015-12-22 on
                  │                           on branch "master".
                  └── [all-files]             Report on all files in this revision
                      ├── README              Summary of files in [all-files]
                      ├── author_ext_files.csv Number of files of given extension in which author has code
                      ├── author_ext_loc.csv  Number of LoC author in files of given extension by author
                      ├── [all-authors]       Sub-report on all authors
                      │   ├── README          Summary of files in [all-authors]
                      │   ├── code-age.png    Graph of code age. LoC / day vs date
                      │   ├── code-age.txt    List of commits in the peaks in the code-age.png graph
                      │   ├── details.csv     LoC in each directory in for these files and authors
                      │   ├── newest-commits.txt List of newest commits for these files and authors
                      │   └── oldest-commits.txt List of oldeswest commits for these files and authors
                ....
                      ├── Alex_Henrie         Sub-report on author Alex Henrie
                      │   ├── README
                      │   ├── code-age.png
                      │   ├── code-age.txt
                      │   ├── details.csv
                      │   ├── newest.txt
                      │   └── oldest.txt


### A closer look at [2015-12-29.28274d02.master/\[all-files\]](https://github.com/peterwilliams97/git-stats-examples/tree/master/examples/git.stats/git/reports/2015-12-29.28274d02.master/%5Ball-files%5D)

This directory contains files that report on the age of all authors code for all files (i.e. every
file) in revision `28274d02`, the `git` repository `master` branch on 2015-12-29.

##### 1) [code-age.png](https://github.com/peterwilliams97/git-stats-examples/blob/master/examples/git.stats/git/reports/2015-12-29.28274d02.master/%5Ball-files%5D/%5Ball-authors%5D/code-age.png) is a graph showing the age of the code in question.

The horizontal axis is date and the vertical axis is LoC /day. This means the area under the curve
between two dates is the LoC surviving from the period bounded by those datess.

You can see that some code from 2006 survives in the current git master branch.

![Age graph](https://github.com/peterwilliams97/git-stats-examples/blob/master/examples/git.stats/git/reports/2015-12-29.28274d02.master/%5Ball-files%5D/%5Ball-authors%5D/code-age.png)


##### 2) [code-age.txt](https://github.com/peterwilliams97/git-stats-examples/blob/master/examples/git.stats/git/reports/2015-12-29.28274d02.master/%5Ball-files%5D/%5Ball-authors%5D/code-age.txt) lists the commits in the peaks in code-age.png

    ================================================================================
    [all-authors]: 10 peaks 117654 LoC
    ................................................................................
      5) 187 commits 12253 LoC around 2007-07-18
     1025 LoC, 2007-07-21 90a7149 German translation for git-gui
     1006 LoC, 2007-07-22 e79bbfe Add po/git-gui.pot
      992 LoC, 2007-07-22 4fe7626 Italian translation of git-gui
     1095 LoC, 2007-07-25 2340a74 Japanese translation of git-gui
     1150 LoC, 2007-07-27 f6b7de2 Hungarian translation of git-gui
    ................................................................................
     10) 130 commits 9705 LoC around 2009-06-03
      135 LoC, 2009-05-26 3902985 t5500: Modernize test style
     7040 LoC, 2009-06-01 f0ed822 Add custom memory allocator to MinGW and MacOS builds
      124 LoC, 2009-06-04 195643f Add 'git svn reset' to unwind 'git svn fetch'
      127 LoC, 2009-06-06 2264dfa http*: add helper methods for fetching packs
      288 LoC, 2009-06-06 5424bc5 http*: add helper methods for fetching objects (loose)
    ................................................................................
        ...

##### 3) [oldest-commits.txt](https://github.com/peterwilliams97/git-stats-examples/blob/master/examples/git.stats/git/reports/2015-12-29.28274d02.master/%5Ball-files%5D/%5Ball-authors%5D/oldest-commits.txt) lists the oldest commits in the code in question.

    ================================================================================
    Guido van Rossum: 2109 commits 78288 LoC
    ................................................................................
     3760 LoC, 1990-10-14 daadddf Initial revision
      802 LoC,   Modules/cstubs
      599 LoC,   Parser/pgen.c
      383 LoC,   Modules/cgen.py
    ................................................................................
       16 LoC, 1990-10-15 fddb56c Adde dconvenience functions.
       16 LoC,   Python/errors.c
    ................................................................................
        3 LoC, 1990-10-15 5122aee Made exception objects extern. Added convenience functions.
        3 LoC,   Include/pyerrors.h

        ...

##### 4) [newest-commits.txt](https://github.com/peterwilliams97/git-stats-examples/blob/master/examples/git.stats/git/reports/2015-12-29.28274d02.master/%5Ball-files%5D/%5Ball-authors%5D/newest-commits.txt) lists the oldest commits in the code in question.

    ================================================================================
    [all-authors]: 23743 commits 764802 LoC
    ................................................................................
       12 LoC, 2015-12-29 28274d0 Git 2.7-rc3
       11 LoC,   Documentation/RelNotes/2.7.0.txt
        1 LoC,   GIT-VERSION-GEN
    ................................................................................
      119 LoC, 2015-12-28 c5e5e68 l10n: Updated Bulgarian translation of git (2477t,0f,0u)
      119 LoC,   po/bg.po
    ................................................................................

       ...

##### 5) [details.csv](https://github.com/peterwilliams97/git-stats-examples/blob/master/examples/git.stats/git/reports/2015-12-29.28274d02.master/%5Ball-files%5D/%5Ball-authors%5D/details.csv) attempts to show where the code is distributed through the source tree.

<table>
<tr><th>dir</th><th>LoC</th><th>frac</th></tr>
<tr><td></td><td>78288</td><td>0</td></tr>
<tr><td>Modules</td><td>33059</td><td>0.422274167178</td></tr>
<tr><td>Objects</td><td>17963</td><td>0.22944768036</td></tr>
<tr><td>Python</td><td>13024</td><td>0.166360106274</td></tr>
<tr><td>Include</td><td>4256</td><td>0.0543633762518</td></tr>
<tr><td>PC</td><td>3583</td><td>0.045766911915</td></tr>
<tr><td>Parser</td><td>3248</td><td>0.0414878397711</td></tr>
</table>

* The source tree of Guido's C files contains 78288 LoC
* Its subdirectory `Modules` contains 33059 LoC
* etc


### Top level files [2015-12-22.4120e146.2_7/__c.__cpp.__h/](https://github.com/peterwilliams97/git-stats/tree/master/examples/git.stats/cpython/reports/2015-12-22.4120e146.2_7/__c.__cpp.__h/)

##### 1) [ext_author_files.csv](https://github.com/peterwilliams97/git-stats/blob/master/examples/git.stats/cpython/reports/2015-12-22.4120e146.2_7/__c.__cpp.__h/ext_author_files.csv) shows numbers of source files by extension and author

<table><tr><th></th><th>Total</th><th>Guido van Rossum</th><th>Martin v. Löwis</th><th>Tim Peters</th><th>Neal Norwitz</th></tr><tr><th>Total</th><th>15092</th><th>3252</th><th>1239</th><th>962</th><th>770</th></tr><tr><th>.c</th><th>12887</th><th>2744</th><th>1013</th><th>829</th><th>708</th></tr><tr><th>.h</th><th>2205</th><th>508</th><th>226</th><th>133</th><th>62</th></tr></table>

This shows the number of files in which each author has one or more lines of code in the revision
being reported. (This table shown on this page is truncated.)

##### 2) [ext_author_loc.csv](https://github.com/peterwilliams97/git-stats/blob/master/examples/git.stats/cpython/reports/2015-12-22.4120e146.2_7/__c.__cpp.__h/ext_author_loc.csv) shows LoC by extension and author

<table><tr><th></th><th>Total</th><th>Jack Jansen</th><th>Guido van Rossum</th><th>Martin v. Löwis</th><th>Thomas Heller</th></tr><tr><th>Total</th><th>549292</th><th>79897</th><th>78288</th><th>49728</th><th>25848</th></tr><tr><th>.c</th><th>464959</th><th>79578</th><th>70939</th><th>40661</th><th>22891</th></tr><tr><th>.h</th><th>84333</th><th>319</th><th>7349</th><th>9067</th><th>2957</th></tr></table>

This shows the lines of code in the revision being reported. (This table shown on this page is truncated.)

### code-age.py usage

* Copy code-age.py to your computer
* Open a shell and cd to the root of the git repository you want to report
* `python code-age.py` NOTE: This can take hours to run a big repository as it blames every file in the repository.
* The location of the reports directory will be written to stdout
* Optionally try some patterns e.g. `python code-age.py '*.py'`, `python code-age.py docs`

