“Challenges I Faced as a Beginner & How I Solved Them”
My Git Learning Journey — Problems I Faced & How I Solved Them

When I started learning Git and GitHub, I faced several beginner issues. These problems taught me how Git actually works behind the scenes. Here are the key challenges and how I resolved them.

1. Error: “src refspec main does not match any”
Why it happened: I tried to push to the main branch before creating any commits. Git only creates a branch after the first commit.

How I solved it: I staged and committed my files:

Code
git add .
git commit -m "initial commit"
git branch -M main
git push -u origin main

This created the main branch and allowed the push.

2. Permission denied (403) when pushing to GitHub
   
Why it happened: I was using my GitHub password. GitHub no longer accepts passwords for Git operations.

How I solved it: I created a Personal Access Token (PAT) with the correct repo permissions and used it instead of a password.

3. Accidentally turned my entire HOME folder into a Git repository
   
Why it happened: I mistakenly ran git init in my home directory (~). This caused Git to track everything — including personal folders like Devops-learning.
Symptoms:
•	Personal folders appeared on GitHub
•	Git behaved unpredictably
•	Wrong files were pushed

How I solved it:
I removed the accidental Git repo:

Code
cd ~
rm -rf .git
Then I created a clean project folder:
Code
mkdir git-calculator
cd git-calculator
git init

4. Remote contains work that you do not have locally
   
Why it happened: My GitHub repo had old commits from the accidental home-directory repo. My new clean project had different commits, so Git refused to push.
How I solved it: I deleted the old GitHub repo and pushed again from my clean folder:

Code
git push -u origin main
This created a fresh, clean repository.

5. Final Clean Setup
After fixing everything, I now follow this clean workflow:

Code
git init
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin <repo-url>
git push -u origin main

 What I Learned
•	Always run git init inside the project folder
•	Git needs at least one commit before pushing
•	PAT tokens are required for GitHub authentication
•	The remote URL is where you push, the branch name is what you push
•	A clean folder structure avoids accidental pushes
•	Git errors always have a logical reason
