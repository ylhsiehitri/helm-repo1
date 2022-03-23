# Setup helm repo & chart artifact creation

* Setting for Github Pages

github repo --> Settings --> Pages --> Source: `branch` as `main`, and `folder` as `docs`

* Download from github
```console
git clone git@github.com:ylhsiehitri/helm-repo1.git
cd helm-repo1
```

* Make directory for GitHub Pages site
```console
# There should already be the directory "docs", otherwise create it
mkdir docs
# Optional: index.html is the home page of GitHub Pages site, without this file, will show 404. It is fine.
vi docs/index.html
```

* Create chart (example: create a chart of name "cu")
```console
helm create cu
helm package cu
mv cu-0.1.0.tgz ./docs
# helm repo index <dir> --url <url>: create the index.yaml in <dir>, the <url> is the GitHub Pages site, which would be used in index.yaml
helm repo index docs --url https://ylhsiehitri.github.io/helm-repo1
```

* Push back to github
```console
git add -i
git commit
git push
```

# Install the chart from repo

* Add and update helm repo
```console
helm repo add helm-repo1 https://ylhsiehitri.github.io/helm-repo1
helm repo update
```

* Install chart
```console
helm install helm-repo1/cu
```

# Appendix

GitHub Pages site `https://ylhsiehitri.github.io/helm-repo1/` 亦即 `https://github.com/ylhsiehitri/helm-repo1/docs`
