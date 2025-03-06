### ℹ️ About
Cut & Paste Lines (from|to) file without $TEMPFILE even if another process is writing to it. You can also probably use [pv](https://www.ivarch.com/programs/pv.shtml) to do the same more reliably.

### 🖳 Installation
Use [soar](https://github.com/pkgforge/soar) & Run:
```bash
soar add 'cutlines#github.com.pkgforge-security.cutlines'
```

### 🧰 Usage
```mathematica
❯ cutlines --help
Cut & Paste Lines (from|to) file without $TEMPFILE even if another process is writing to it

Options:
  -l, --lines int
        Number (n) of lines to cut
  -f, --file string
        Input file to cut lines from
  -o, --output string
        Output file to paste cut lines (Use /dev/null if output is unneeded)
  -p, --print
        Print the lines that are cut to stdout
  -q, --quiet
        Quiet mode (Suppress Info & Stats)

 ~> #Cut 100,000 lines from input.txt, paste it in output.txt
  ❯ cutlines --lines 100000 --file input.txt --output output.txt

 ~> #Same as above but be completely quiet
  ❯ cutlines --lines 100000 --file input.txt --output output.txt --quiet

 ~> #Same as above but be pipe friendly by printing lines to stdout
  ❯ cutlines --lines 100000 --file input.txt --output /dev/null --print --quiet

 ~> !! #By specifying a value for --lines larger than total lines of --file input.txt, you will completetly cut all lines from input.txt
 ~> !! #Use tee | >> instead of -o | --output flags, as files WILL GET CORRUPTED if they are being written using os file locks.
```