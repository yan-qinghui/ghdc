# One-Click Transfer of DockerHub Images to GitHub Container Registry (GHCR.IO)

## Project Introduction

This project utilizes GitHub Actions to **automatically transfer DockerHub images to the GitHub Container Registry (GHCR.IO)**. This prevents issues with image access due to blocking or retraction, ensuring the safety and reliability of your image resources.
You can leverage GitHub's **free 2000 minutes of private repository runtime per month** or use a public repository for **unlimited runtime**. Additionally, using the **Nanjing University Open Source Mirror** accelerates the pulling of GHCR.IO images within China.

## Usage Steps

### 1. Clone the Project to Your GitHub Repository

Please do not use Fork! Forked repositories have limitations on GitHub Actions runtime. Instead, import the project using Git:

1. Click this link to go to GitHub's import page: [GitHub Import Page](https://github.com/new/import)
2. In the "Your old repository's clone URL" field, enter:
   ```
   https://codeberg.org/fossandroid/dockerhub2ghcr.git
   ```
3. Follow the prompts to complete the project import.

### 2. Manually Trigger GitHub Actions

#### Steps:

1. Go to your GitHub repository and click the "**Actions**" tab at the top of the page.

2. In the left sidebar, find the "**DockerHub image copied to GHCR.IO**" workflow and click it. (Note: "DockerHub image copied to GHCR.IO" translates to "Copy DockerHub Image to GHCR.IO")

3. Click the "**Run workflow**" button on the upper right corner. This will display a form to input parameters.

4. Fill in the following parameters in the popup:
   - **dockerhub_image**: The DockerHub image name (default is `nginx`), e.g., `alpine` or `python`.
   - **tag**: The image tag, default is `latest`. You can specify a version like `1.0`.
   - **ghcr_image**: The desired name of the image you want to push to GHCR.IO, such as `myimage`.

5. After filling in the parameters, click the "**Run workflow**" button. GitHub Actions will automatically run, syncing your specified DockerHub image to GHCR.IO.

#### Example Parameter Values:

- **dockerhub_image**: `nginx`
- **tag**: `latest`
- **ghcr_image**: `my-nginx`

Upon completion, GitHub Actions will automatically pull the DockerHub image and push it to GHCR.IO.

### 3. Accelerated Image Pulling in China

To speed up image downloads in China, you can use Nanjing University's Open Source Mirror. Simply replace `ghcr.io` with `ghcr.nju.edu.cn` when pulling images:

```bash
docker pull ghcr.nju.edu.cn/<your-username>/<your-image>:<tag>
```

This significantly improves the speed of pulling images from GHCR.IO within China.

## Advantages

- **Prevents Image Retraction or Blocking**: Syncing to a private GHCR.IO repository ensures continued access even if the original image is retracted or blocked.
- **Free Use of GitHub Container Service**:  2000 free minutes of private repository runtime per month, or unlimited runtime for public repositories.
- **Accelerated Domestic Mirror**: Using Nanjing University's mirror makes pulling images from GHCR.IO faster and more stable within China.